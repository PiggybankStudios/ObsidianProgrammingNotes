## Links
* https://ziglang.org/
* https://ziglang.org/documentation/0.13.0/
* https://ziglang.org/documentation/master/std/
* https://ziglang.org/learn/build-system/
* https://andrewkelley.me/
* https://ziglang.org/documentation/master/#Builtin-Functions
## TODO List
- [ ] **How do we handle multiple files in zig?**
	- We can `@import("file.zig")`, but then it's entire contents go in a const variable, like a namespace. No way to put everything directly in this file's namespace
	- We can unwrap inner namespaces for each file, like `const GameState = Game.GameState;` so if things are getting especially annoying to type out we can shorten things. But we have to do this shortening for every single file
	- Only `pub` functions are exposed when `@import`ing a file. Can we make two files "friends" where they share access to non-public types?
	- Seems like we can `@import` a file and not get unused errors if we don't use it
	- https://www.reddit.com/r/Zig/comments/143oofw/shortening_the_imports/
	- If we put public functions and things directly in the file, the file itself can act like a "struct"?
	- If a top-level files @imports other files, when we import that top-level, can it be like the "index" into the library?
- [ ] Make a global structure to hold our state
- [ ] Get a shared library working with **C/C++** and **Zig**
- [ ] Figure out Vectors and Rectangles in Zig
- [ ] Follow Vulkan example to get single triangle rendering in GLFW window https://github.com/slimsag/mach-glfw-vulkan-example
- [ ] Get keyboard and mouse input from GLFW
- [ ] Checkout Mason Ramaley's GLFW wrapper? https://github.com/Games-by-Mason/glfw-zig
## Random Notes
- [x] Zig Version: zig-windows-x86_64-**0.14.0-dev.2424**+7cd2c1ce8 downloaded Dec 9th 2024
- Zig Version: zig-windows-x86_64-**0.13.0** downloaded Dec 14th 2024
- To disable runtime safety in a block, call `@setRuntimeSafety(false);` (allows for integer overflow/underflow etc.)
- Convert an integer to a pointer: `@ptrFromInt(int_value);`
- Pointers are `*T`, optional pointers are `?*T`
- To unwrap an optional, you can use if or while like `if (optional) |value| { ... }`. You can also use `orelse` keyword after something that returns an optional
- Modulo operator is now `@mod(value, divisor)` not `%` character
- To initialize a variable without clearing it to 0, you can use `= undefined` keyword
- `defer` can be used to defer some line to be called when the scope exits
- `errdefer` can be used to defer some line to be called if the scope exits with an error return
- The keyword `try` is a shortcut for `catch |err| return err;`
- You can do `catch unreachable` to basically assert that no errors should occur
- Format strings use `{` and `}` characters so they need to be doubled up to actually output them in the result like `{{` and `}}`
- Custom test runner https://www.openmymind.net/Using-A-Custom-Test-Runner-In-Zig/ - https://gist.github.com/karlseguin/c6bea5b35e4e8d26af6f81c22cb5d76b
- Use `zig build run` to make the `run` step execute
- Add `--summary all` to zig invocation to get a summary of the steps in the build graph
- https://github.com/ziglang/zig/blob/master/doc/build.zig.zon.md
## Naming Conventions
* **Basic Types** = `u8`, `i32`, `f64`, `bool`, etc.
* **Structs** = `UpperCamelCase`
* **Functions** = `camelCase(...)`
* **Builtins** = `@camelCase(...)` except the following: `@FieldType`, `@This`, `@Type`, `@TypeOf`, `@Vector`
* **Globals** = ?
* **Constants** = ? (as in very obvious values that are given a name, like Pi, not any variable with `const` keyword)
* **Imported Constants** = `const UpperCamelCase = @import(...);` (i.e. same as **Structs**)
* **Variables** = `camelCase` (optional unwrapped variables have `_leadingUnderscore`)
* **Struct Members** = `camelCase`
* **Enums** = `camelCase`?
* **Test Names** = `"lowercase_with_underscores"` (we could allow spaces, but debug output includes module name and namespace with periods)
* **init**, **create**, **destroy**, **deinit**
	* `create`/`destroy` is used to indicate a `T: type` is part of the allocation call in `Allocator`. When inside our own structure they often mean combined allocation+init or deinit+free in one function
	* `init`/`deinit` inside our own structs indicate initialization of fields only, not allocation (unless inner fields need allocation/deallocation)
* **File Names** = `lowercase_with_underscores.zig` (because Windows file system doesn't treat capitalization as important)
* **Argument Ordering**
	1. **self** (For member functions)
	2. **allocator** (if needed)
	3. **comptime T: type** (generic functions)
	4. **directObject** (the main thing being operated on)
	5. ...
## Useful Functions/Types in `std`
- `std.debug.captureStackTrace(...) std.builtin.StackTrace`:  can be used to capture the stack trace, and then printed later with `std.debug.dumpStackTrace(trace)`
- `std.debug.print(format, args)`
- `std.debug.assert(condition)`
- `std.testing.expect(condition)`
- `std.fs.cwd()`: Gets the current working directory of the program
- `std.fs.cwd().openFile(path, options)` or `std.fs.cwd().createFile(path, options)`
## String Types (really "slice", "array", and "pointer" types)
- `[]u8`: A slice of type `u8`. Can access `.len` and `.ptr`
- `[5]u8`: An array of type `u8` with 5 elements. Can access comptime `.len` (not `.ptr`). `&x` produces `*const [5]u8`
- `[]const u8`: A slice with const applied to the ptr. If you have a `x: []u8` and you do `&x` it will become `*const []u8` which will then coerce into this
- `[_]u8`: An array of length that will be determined by following `{ }` initialization syntax
- `[c]u8`: C-Style String??
- `[:0]u8`: A null-terminated slice using 0 for termination. Known length, can access `.len` and `.ptr`
- `[*:0]u8`: A null-terminated pntr of unknown length. **TODO:** Can we calculate length easily through some std func?
- `*const []u8`: A const pointer to a slice of `u8`. The result of doing `&` on an array of `u8`. Can coerce to `[]const u8`
- `[5:0]u8`: A null-terminated array of length 5. Can access comptime `.len` and `.ptr`
- To initialize a null-terminated array of bytes you have to omit the type on the left of the `=` and use `[_:0]u8` before curly bracket init `{ 1, 2 }`
	* `const str = [_:0]u8{ 1, 2 };`
- To turn an array into a slice, you must have const after the `[]` and you must do `&` operator on array
	* `const array: [5]u8 = .{1, 2, 3, 4, 5};`
	* `const slice: []const u8 = &array;`
- Array lengths must be **comptime** known
## Builtin Functions [Link](https://ziglang.org/documentation/master/#Builtin-Functions)
- `@addWithOverflow(a, b)` - Performs a + b and returns a tuple with the result and a possible overflow bit. 
- `@alignCast(ptr)` - ptr can be `*T`, `?*T`, or `[]T`. Changes the alignment of a pointer. The alignment to use is inferred based on the result type. 
- `@alignOf(T)` - This function returns the number of bytes that this type should be aligned to for the current target to match the C ABI.
- `@as(T, expression)` - Performs Type Coercion. This cast is allowed when the conversion is unambiguous and safe, and is the preferred way to convert between types, whenever possible. 
- `@atomicLoad` - ?
- `@atomicRmw` - ?
- `@atomicStore` - ?
- `@bitCast` - ?
- `@bitOffsetOf` - ?
- `@bitSizeOf` - ?
- `@branchHint` - ?
- `@breakpoint` - ?
- `@mulAdd` - ?
- `@byteSwap` - ?
- `@bitReverse` - ?
- `@offsetOf` - ?
- `@call` - ?
- `@cDefine` - ?
- `@cImport` - ?
- `@cInclude` - ?
- `@clz` - ?
- `@cmpxchgStrong` - ?
- `@cmpxchgWeak` - ?
- `@compileError` - ?
- `@compileLog` - ?
- `@constCast` - ?
- `@ctz` - ?
- `@cUndef` - ?
- `@cVaArg` - ?
- `@cVaCopy` - ?
- `@cVaEnd` - ?
- `@cVaStart` - ?
- `@divExact` - ?
- `@divFloor` - ?
- `@divTrunc` - ?
- `@embedFile` - ?
- `@enumFromInt` - ?
- `@errorFromInt` - ?
- `@errorName` - ?
- `@errorReturnTrace` - ?
- `@errorCast` - ?
- `@export` - ?
- `@extern` - ?
- `@field` - ?
- `@fieldParentPtr` - ?
- `@FieldType` - ?
- `@floatCast` - ?
- `@floatFromInt` - ?
- `@frameAddress` - ?
- `@hasDecl` - ?
- `@hasField` - ?
- `@import` - ?
- `@inComptime` - ?
- `@intCast` - ?
- `@intFromBool` - ?
- `@intFromEnum` - ?
- `@intFromError` - ?
- `@intFromFloat` - ?
- `@intFromPtr` - ?
- `@max` - ?
- `@memcpy` - ?
- `@memset(slice, value)` - Sets all values in the slice to a specified value
- `@min` - ?
- `@wasmMemorySize` - ?
- `@wasmMemoryGrow` - ?
- `@mod` - ?
- `@mulWithOverflow` - ?
- `@panic` - ?
- `@popCount` - ?
- `@prefetch` - ?
- `@ptrCast` - ?
- `@ptrFromInt(integer) *T` - Converts an integer into a pointer. Return type is inferred so must be known, or @as used to decide type
- `@rem` - ?
- `@returnAddress` - ?
- `@select` - ?
- `@setEvalBranchQuota` - ?
- `@setFloatMode` - ?
- `@setRuntimeSafety` - ?
- `@shlExact` - ?
- `@shlWithOverflow` - ?
- `@shrExact` - ?
- `@shuffle` - ?
- `@sizeOf` - ?
- `@splat` - ?
- `@reduce` - ?
- `@src` - ?
- `@sqrt` - ?
- `@sin` - ?
- `@cos` - ?
- `@tan` - ?
- `@exp` - ?
- `@exp2` - ?
- `@log` - ?
- `@log2` - ?
- `@log10` - ?
- `@abs` - ?
- `@floor` - ?
- `@ceil` - ?
- `@trunc` - ?
- `@round` - ?
- `@subWithOverflow` - ?
- `@tagName` - ?
- `@This` - ?
- `@trap` - ?
- `@truncate` - ?
- `@Type` - ?
- `@typeInfo(type) builtin.Type` - Returns the type info for a type, which can allow reflection of it's members and other information
- `@typeName(type) *const [N:0]u8` - Returns the name of the type as a string
- `@TypeOf(variable...) type` - A special builtin function that takes any (non-zero) number of expressions as parameters and returns the type of the result
- `@unionInit` - ?
- `@Vector` - ?
- `@volatileCast` - ?
- `@workGroupId` - ?
- `@workGroupSize` - ?
- `@workItemId` - ?
