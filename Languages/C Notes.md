## Notes
- [ ] No function overloads?
- [ ] No operator overloading?
- [ ] Do we need to use `/Zc:__STDC__` for MSVC compiler in order to use C23 "properly"
- [ ] MSVC Compiler [Predefined Macros](http://msdn.microsoft.com/en-us/library/b0084kay.aspx) like `_MSC_VER` [Link](https://sourceforge.net/p/predef/wiki/Compilers/#microsoft-visual-c) 
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
## C89 Features/Restrictions
- [ ] 
## C99 Features/Restrictions
- [ ] 
## C11 Features/Restrictions
- [ ] 
## C23 Features/Restrictions
- [ ] https://en.cppreference.com/w/c/compiler_support/23
- [ ] [Static Assert](https://en.cppreference.com/w/c/language/_Static_assert)
- [ ] [Binary Integer Constants](https://en.cppreference.com/w/c/language/integer_constant)
- [ ] [Labels](https://en.cppreference.com/w/c/language/statements#Labels) for declarations and end of blocks
- [ ] Digit Separators
- [ ] `#elifdef` and `#elifndef`
- [ ] [`__has_include`](https://en.cppreference.com/w/c/preprocessor/include) in preprocessor conditionals
- [ ] [`typeof` and `typeof_unqual`](https://en.cppreference.com/w/c/language/typeof)
- [ ] [`__VA_OPT__`](https://en.cppreference.com/w/c/preprocessor/replace#Function-like_macros)