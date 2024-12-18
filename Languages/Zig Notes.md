## Links
* https://ziglang.org/
* https://ziglang.org/documentation/0.13.0/
* https://ziglang.org/documentation/master/std/
* https://ziglang.org/learn/build-system/
* https://andrewkelley.me/
## TODO List
- [ ] 
## Naming Conventions
* **Basic Types** = `u8`, `i32`, `f64`, `bool`, etc.
* **Structs** = `UpperCamelCase`
* **Functions** = `camelCase(...)`
* **Builtins** = `@camelCase(...)` except the following: `@FieldType`, `@This`, `@Type`, `@TypeOf`, `@Vector`
* **Globals** = ?
* **Constants** = ? (as in very obvious values that are given a name, like Pi, not any variable with `const` keyword)
* **Variables** = `camelCase` (optional unwrapped variables have `_leadingUnderscore`)
* **Struct Members** = `camelCase`
* **Enums** = `camelCase`?
* **Test Names** = `"lowercase_with_underscores"` (we could allow spaces, but debug output includes module name and namespace with periods)
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
