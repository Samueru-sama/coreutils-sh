# coreutils-sh

coreutils using pure sh (not bash)

Not fully POSIX since they depend on reading `/proc`

---

Some interesting features: 

* **which** - On GNU `which` when you run `which -a bin1 bin2` if either `bin1` or `bin2` is missing, it will return a `0` exit code. This should not happen and instead this implementation of which will always exit with `1` unless all given arguments are found. 

* **uname** - On both BusyBox and GNU `uname`, a final GNU/Linux or Linux string gets compiled into the binary gets printed when using the `--all` flag, this is flawed since you can compile a static uname in GNU/linux and run it on a non GNU/linux system. To avoid this issue this implementation of `uname` will attempt to read the host `ldd` to correctly determine if the system is GNU/Linux. 
