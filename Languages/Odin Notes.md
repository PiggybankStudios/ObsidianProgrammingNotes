- [ ] MacBook Pro: Downloaded **MacOS ARM64** on *July 20th 2026* version: `dev-2026-07-nightly:819fdc7`
- [ ] Ubuntu Laptop: Downloaded **Linux AMD64** on *August 1st 2026* version: `dev-2026-07-nightly:819fdc7`
- [ ] Windows Desktop: Downloaded **Windows AMD64** on *August 1st 2026* version: `dev-2026-07-nightly:819fdc7` (updated from `dev-2022-12-nightly:521ed286`)
- [ ] Semicolons optional
- [ ] Basic types: `u8`, `f32`, `int`
- [ ] [[odin_help_build.txt]] 
- [ ] **Loops:** (Use labeled loop `label: for cond { }`)
```rust
for { } //Infinite loop
for i < 10 { } //while
for i in 0..<10 { } //exclusive range (0..=10 for inclusive)
for key, value in map { } //Loop over map keys and values
for value, index in array { } //Loop over array with indices
for _, index in array { array[i] = array[i]*2; } //Loop indices to allow mutation in loop
```
- [ ] **Switch statement:** (Also `fallthrough`, range-based cases `case 0..=10:`)
```rust
#partial switch ODIN_ARCH {
	case .i386: fmt.println("32-bit Intel")
	case .arm64: fmt.println("64-bit ARM")
	case .amd64: fmt.println("64-bit Intel (x86_64)")
	case: fmt.println("Unhandled architecture")
}
```
- [ ] **Defer keyword:** (reverse order of declared)
```rust
{
	defer fmt.println("End of scope!")
	defer {
		fmt.println("3nd to last")
		fmt.println("2nd to last")
	}
	defer 
	fmt.println("Before end!")
}
```
- [ ] **when statement:** (Evaluated at compile-time, no scopes, allowed at file scope)
```rust
when ODIN_ARCH==.i386 { ... }
else when ODIN_ARCH=.amd64 { ... }
else { ... }
```
- [ ] **Procedures:**
```rust
myFunc :: proc(a: int, b: f32) -> (f32) { return a*b }
sum :: proc(nums: ..int) -> (result: int) {
	result = 0;
	for n in nums { result += n }
	return
}
sum(1, 2, 3, 4); sum(..arrayVar)
foobar :: proc(in1: int, in2: f32) -> (int) { return in1; }
foobar :: proc() -> (a, b: int) { b = 10; a = 20; return }
func1 :: proc(a: int) { ... }
func2 :: proc(a: f32) { ... }
func3 :: proc(a: u8) { ... }
func :: proc{ func1, func2, func3 }
```
- [ ] 