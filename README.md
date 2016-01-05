GYP can Generate Your Projects.
===================================

This fork of the upstream GIT repo at Google has 2 additional features:

1. The xcode generator recognizes the full set of build variables
that correspond to the set of destination names for the copy phase,
as appears in the Xcode UI. Do
 ```
 git diff upstream_master xcode_changes
 ```
 to see the list. The original version only understands
 the variable `$(BUILD_PRODUCTS_DIR)` which corresponds to
 'Products Directory'.

    All GYP xcode tests that pass on upstream_master pass with these
    changes. (There are 5 tests that fail in both cases.)

2. The msvs generator supports the Emscripten vs-tool plug-in.
That is, it recognizes the properties vs-tool offers to
control the Emscripten compiler and linker. These properties
can be included in an `msvs_settings` dictionary. Note this feature
has only been tested with Visual Studio 2010.

    All GYP msvs tests are expected to still pass. That will be tested soon.
    

The first of these has been submitted to Google but they want
tests, that I have not had time to write, before merging. The
same lack of tests prevents submission of the second.

GYP is a Python application requiring Python 2.7.

To install, clone the repo to your machine and run the following
commands in a shell:

```bash
cd <your_gyp_clone>; sudo ./setup.py install
```

On Windows, use either a Git Bash or Cygwin Bash shell and omit the
`sudo`. Alternatively enter the following commands at a Windows Command
Prompt (`cmd.exe`):

```cmd
cd <your_gyp_clone>
python setup.py install
```

Documents are available at [gyp.gsrc.io](https://gyp.gsrc.io), or you
can check out the ```md-pages``` branch to read those documents offline.

### Installing Python 2.7

Visit the [Python Downloads](https://www.python.org/downloads/) page
to learn how to install Python for your OS.

On Windows you can use either the [native Windows version](https://www.python.org/downloads/windows/)
(recommended) or the version found in [Cygwin](https://www.cygwin.com).

If you install the native Windows version you must add `<python>` and
`<python>/Scripts` to the PATH environment in Windows. `<python>` represents
your actual install directory which defaults to `C:\Python27`.
