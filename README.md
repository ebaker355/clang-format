# clang-format

This is a patch to clang-format 3.7.0 which adds an option to insert a
space between the return type and the method name for Objective-C.

This:

    `- (NSString *)method;`

Becomes:

    `- (NSString *) method;`

The option is OFF by default. To enable, add this line to your `.clang-format`
file:

    `ObjCSpaceBeforeMethodDeclaration: true`

I am using this binary with this Xcode plugin:
https://github.com/travisjeffery/ClangFormat-Xcode

This build should not mangle your code, but use at your own risk. If you do have
issues, please let me know.

Enjoy!
