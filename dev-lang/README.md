# Notice

This patch is intended for people who want to install Python 3.11 alongside Python 3.10 on a clang/musl system.

[This PR to Python](https://github.com/python/cpython/pull/24502) broke building with a stock version of clang, as, by default, `clang -print-multiarch` displays `x86_64-linux-gnu` regardless of libc, causing a configure error during the "checking for multiarch" step in Python 3.11. If you only want to use Python 3.11, the `sys-devel/clang` patch (sourced from https://github.com/llvm/llvm-project/issues/51469) should be all you need, as now prints `x86_64-linux-musl`, pleasing Python 3.11's configure.

Python 3.10 doesn't do any musl checks, so the wrong `clang -print-multiarch` output lets the build run through. However, fixing `clang -print-multiarch`'s output causes Python 3.10 to see an unexpected multiarch value, [causing its configure to fail](https://bugs.gentoo.org/862888#c5). This patch, therefore, backports the musl check from Python 3.11 to 3.10, so fixed Clang can build Python 3.10.

If you want just Python 3.10, the technically wrong `clang -print-multiarch` output will let you use Python 3.10 mostly without issues (the major one is `pip` installing binary wheels built against glibc).

Therefore, _only use this patch if you want to use both Python 3.11 and 3.10_ (or don't want libraries ending with `gnu.so` in your disk).

# Important

Remember to reemerge packages built against Python 3.10 after applying this patch with `emerge -1 /usr/lib/python3.10/site-packages` (otherwise, no Python 3.10 script using FFIs will work).
