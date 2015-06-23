# clang-format

This is a patch to clang-format 3.7.0 which adds several additional formatting
options:


###ObjCSpaceBeforeMethodDeclaration (bool)
If `true`, inserts a space between the return type and the method name for
Objective-C.

This:

    - (NSString *)method;

Becomes:

    - (NSString *) method;

This option is OFF by default. To enable, add this line to your `.clang-format`
file:

    ObjCSpaceBeforeMethodDeclaration: true


###BreakBeforeElse (bool)
If `true`, will place a break before 'else', like the `Stroustrup` code style.

This:

    if (condition) {
        ...
    } else {
        ...
    }

Becomes:

    if (condition) {
        ...
    }
    else {
        ...
    }

This option is OFF by default. To enable, add this line to your `.clang-format`
file:

    BreakBeforeElse: true

###BreakBetweenDoWhile (bool)
If `true`, adds a break before `while` in a 'do...while' loop.

This:

    do {
        ...
    } while (condition);

Becomes:

    do {
        ...
    }
    while (condition);

This option is OFF by default. To enable, add this line to your `.clang-format`
file:

    BreakBetweenDoWhile: true

###ForceEmptyLineAtEOF (bool)
If `true`, ensures that there is always at lease 1 empty line at the end of the
file.

This option is OFF by default. To enable, add this line to your `.clang-format`
file:

    ForceEmptyLineAtEOF: true

###Xcode Plugin

I am using this binary with this Xcode plugin:
https://github.com/travisjeffery/ClangFormat-Xcode

You may download the [binary](https://github.com/ebaker355/clang-format/raw/master/clang-format),
or follow these steps to build your own patched version:

######Most of these steps were taken from http://blog.hardcodes.de/articles/63/building-clang-format-and-friends-on-osx-mountain-lion

    $ export build=~/Programming/clang
    $ mkdir -p $build
    $ cd $build
    $ svn co http://llvm.org/svn/llvm-project/llvm/trunk llvm
    $ cd llvm/tools
    $ svn co http://llvm.org/svn/llvm-project/cfe/trunk clang
    $ cd clang/tools
    $ svn co http://llvm.org/svn/llvm-project/clang-tools-extra/trunk extra
    $ cd $build
    $ git clone https://github.com/ebaker355/clang-format.git clang-format-patch
    $ cd llvm/tools/clang
    $ svn patch $build/clang-format-patch/clang-format.patch
    $ cd $build
    $ mkdir clang
    $ cd clang
    $ ../llvm/configure --enable-libcpp --enable-cxx11 --enable-debug-symbols=no --enable-optimized
    $ make

    The clang-format binary will be in the Release+Asserts/bin directory


This build should not mangle your code, but use at your own risk. If you do have
issues, please [file a report](https://github.com/ebaker355/clang-format/issues).

Enjoy!
