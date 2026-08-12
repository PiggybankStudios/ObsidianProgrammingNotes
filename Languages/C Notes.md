## Notes
- [ ] No function overloads?
- [ ] No operator overloading?
- [ ] Do we need to use `/Zc:__STDC__` for MSVC compiler in order to use C23 "properly"
- [ ] MSVC Compiler [Predefined Macros](http://msdn.microsoft.com/en-us/library/b0084kay.aspx) like `_MSC_VER` [Link](https://sourceforge.net/p/predef/wiki/Compilers/#microsoft-visual-c) 
- [ ] GCC and Clang are actually different compilers, Clang being newer and more fully featured. But gcc.exe installed with MinGW is claiming a "clang" version so idk
- [ ] `bool` and `true`/`false` work just fine in MSVC as long as `stdbool.h` is included
- [ ] [UUID Generation](http://graemehill.ca/minimalist-cross-platform-uuid-guid-generation-in-c++/)
- [ ] [Mixing C and C++ Code](https://isocpp.org/wiki/faq/mixing-c-and-cpp)
- [ ] [fopen vs open](https://www.delftstack.com/howto/c/open-vs-fopen-in-c/)
- [ ] 
## Plan
- [ ] Start a new codebase that is strictly C, not C++
- [ ] Investigate pros/cons of using various C standard versions
- [ ] Decide on a naming convention and function argument ordering
- [ ] Setup a basic tools for metaprogram generation that uses as few dependencies as possible and compiles quickly
- [ ] Decide on folder structure for various core pieces of the system (macros, OS functions, common single header stuff, graphics APIs, etc.)
- [ ] Setup a documentation structure so I can document how things work as I go (as needed). Maybe a changelog too?
##### Work Areas
- [ ] C std lib wrapping
- [ ] Memory Management, Arenas
- [ ] Strings and File Paths
- [ ] VarArray equivalent
## C89 Features
- [ ] 
## C99 Features
- [ ] 
## C11 Features [Link](https://en.cppreference.com/w/c/11) (C17 is purely bug-fixes and clarifications to C11)
- [ ] [MSVC C11 and C17 Support](https://devblogs.microsoft.com/cppblog/c11-and-c17-standard-support-arriving-in-msvc/)
- [ ] `_Static_assert(expression, message) ` NOTE: C11 requires a message, C23 added support for omitting it, and changed to `static_assert` name
- [ ] Removed `gets()`
- [ ] `_Atomic(int)` Atomic types (include `stdatomic.h` for convenient names) [Link](https://en.cppreference.com/w/c/language/atomic) **(MSVC requires `/experimental:c11atomics` flag and still sets `__STDC_NO_ATOMICS__`)**
- [ ] `_Thread_local` (`thread_local` in C23) qualifier (Works on both compilers!)
- [ ] `_Generic(type, list)` Allows an expansion based on type of the first argument to any number of code snippets
## C23 Features [Compiler Support](https://en.cppreference.com/w/c/compiler_support/23)
- [ ] `[[nodiscard]]` added to force caller to store the return value (Actually supported on MSVC despite the cppreference page!)
- [ ] `[[maybe_unused]]`: Basically the same as our `UNUSED(variable)` macro (We don't care)
- [ ] `[[deprecated]]`: Don't care much
- [ ] Attributes in general are added by C23 spec (the 3 things above)
- [ ] IEEE 754 decimal floating-point types (not sure what new floating point types/operations are supported but I don't think I care)
### `[[fallthrough]];` attribute to help catch accidental fallthroughs inside a switch statement (seems to be supported by Clang and MSVC just fine)
- [ ] `u8'c'` u8 character constants (not sure if they are supported in MSVC, didn't test)
- [ ] Labels are allowed on the same line as declarations and also end of a block (don't care)
- [ ] `0b1010101` binary integer constants are now officially supported (but they seemed to work before anyways)
- [ ] Can check if an attribute is supported with `__has_c_attribute(attribute_name)`
- [ ] `int a = 1'000` Single tick characters allowed in integer constants (but Sublime syntax doesn't handle this yet **(fixed!)**)
- [ ] `#elifdef` and `#elifndef` added **(Not supported by MSVC)**
- [ ] UTF-8 string literals changed types from `char[N]` to `char8_t[N]`
- [ ] Support for `#warning` preprocessor keyword **(Not supported by MSVC)**
- [ ] `_BitInt(N)` and `unsigned _BitInt(N)` Bit-precise integer types **(Not supported by MSVC)**
- [ ] `[[noreturn]] void Function() { ... exit(...); }` can be used to annotate functions that don't return (and suffixes for their integer constants)
### `#if __has_include("name.h")` can be used to guard an `#include` statement behind whether the file exists or not [Link](https://en.cppreference.com/w/c/preprocessor/include)
- [ ] Identifiers now conform to *Unicode UAX #31* which gets rid of a bunch of problem codepoints and brings it more in line with other languages (don't care)
- [ ] `= {}` Empty initialization is now supported **(Not supported by MSVC, but `{0}` syntax is!)**
- [ ] `typeof` and `typeof_unqual` to get the type of a variable or expression [Link](https://en.cppreference.com/w/c/language/typeof)
- [ ] Keyword naming conventions `alignas`, `alignof`, `bool`, `static_assert`, `thread_local`
- [ ] Predefined `true` and `false` (Not supported by MSVC, but `stdbool.h` does just fine)
- [ ] `[[unsequenced]]` and `[[reproducible]]` can be used to markup a function [Link](https://en.cppreference.com/w/c/language/attributes/unsequenced) (Don't care much)
- [ ] Relax requirements for variadic parameter list [Link](https://open-std.org/JTC1/SC22/WG14/www/docs/n2975.pdf) (I don't think I care?)
- [ ] Type inference in object definitions [Link](https://open-std.org/JTC1/SC22/WG14/www/docs/n3007.htm) (Maybe I care? But not super important until we check on `_Generic`s)
- [ ] `#embed` Finds a file and replaces the `#embed` macro with an integer list of values based on the contents of the file **(Only supported in Clang 19!)**
- [ ] Enum types are not always `int` anymore, they can therefore support values outside `[INT_MAX, INT_MIN]` range (don't care too much, didn't test)
- [ ] `typedef enum : u8` type specified enums are now supported **(Not supported by MSVC)**
- [ ] `__VA_OPT__(,) __VA_ARGS__` Allows for specifying a leading separator if `__VA_ARGS__` is not empty **(Not supported by MSVC in Desktop version, maybe newer version?)** [Link](https://en.cppreference.com/w/c/preprocessor/replace#Function-like_macros)
- [ ] `nullptr` keyword added **(Not supported by MSVC)**
