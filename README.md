# aubio-python
This repository is providing a compiled version of aubio-python, the Python module for aubio, which is not installed with the installation of the `aubio` package that's in the official Termux repository.

This program was entirely built within Termux on my ARMv8 (aarch64/arm64) phone. 

After many attempts of trying to install from pip didn't bear fruit, I've tried using proot-distro environments (which worked with pip), 
but my goal was to have it working in a vanilla Termux environment.
This build is based on release (v.0.5.0a0) from the Git repo, instead of the one from pypi's v.0.4.9 one.
# installation
It is pretty easy: just extract the tar.gz archive, but make a folder first to unpack.

Assuming that you're in the home folder, make a new directory using `mkdir yourfoldername`, then for extraction you can use: `tar -xf aubio-python-aarch64.tar.gz -C ./yourfoldername`.

The extracted folder matches the layout of the Termux prefix for ease of use.

To make everything easy, it is recommended to use `mc` (Midnight Commander) to copy over the files, just remember to not go 
back from the `com.termux/files` folder (which has `/home` and `/usr` in it).

After copying the files to their own directories, you can try launching aubio by simply typing `./aubio`, which would launch the program.
# troubleshooting
* If you see a message from `tar` saying that `... not found in archive`, use either the `-C ./foldername` or `--directory /path/to/folder` option to extract to a folder.
* If you see a message saying `ModuleNotFoundError: No module named aubio`, investigate if `aubio` and `aubiocut` has "executable" permissions, 
you can test it by going to `/usr/bin` then invoking `./aubio`. If `bash: aubio : Permission denied` is the message you get, use `chmod +x ./aubio` and that should fix the issue.

If you're still experiencing the same message, go to `/usr/lib/python3.11/site-packages/aubio` and repeat `chmod +x` on all the `.py` files and the `.so` file in the directory.
# note
If all done, you should have proper access to the program. However, note that you still need to source `numpy` (dependency for `aubio`) from either the official Termux repo or
installing `numpy` from pip using `MATHLIB="m" pip install numpy`. 
