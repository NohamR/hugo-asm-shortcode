# hugo-asm-shortcode

A Hugo shortcode for displaying assembly code blocks with syntax highlighting, hex bytes, and memory addresses.

## Features

- **Syntax highlighting** for x86 (NASM) and ARM assembly
- **Three display modes:**
  - `raw` - Assembly with syntax highlighting only
  - `hex` - Hex bytes + assembly instruction
  - `full` - Address + hex bytes + assembly instruction
- **Capitalization option** for hex bytes and addresses
- **Dark/light mode** compatible

## Installation

### As a Hugo Module

Add to your `hugo.toml`:

```toml
[module]
  [[module.imports]]
    path = "github.com/NohamR/hugo-asm-shortcode"
```

### Manual Installation

Copy the contents of `module/` to your Hugo site:
- `layouts/shortcodes/asm.html` → your site's `layouts/shortcodes/`
- `assets/css/extended/asm.css` → your site's `assets/css/extended/`

## Usage

### Raw Mode (syntax highlighting only)

```go-html-template
{{</* asm mode="raw" arch="x86" */>}}
mov rax, 1
xor rdi, rdi
syscall
{{</* /asm */>}}
```

### Hex Mode (hex bytes + instruction)

```go-html-template
{{</* asm mode="hex" arch="x86" */>}}
48 c7 c0 01 00 00 00 | mov rax, 1
48 31 ff             | xor rdi, rdi
0f 05                | syscall
{{</* /asm */>}}
```

### Full Mode (address + hex + instruction)

```go-html-template
{{</* asm mode="full" arch="x86" */>}}
00401000 | 48 c7 c0 01 00 00 00 | mov rax, 1
00401007 | 48 31 ff             | xor rdi, rdi
0040100a | 0f 05                | syscall
{{</* /asm */>}}
```

### Parameters

| Parameter    | Default | Description                                      |
|--------------|---------|--------------------------------------------------|
| `mode`       | `raw`   | Display mode: `raw`, `hex`, or `full`            |
| `arch`       | `x86`   | Architecture: `x86` or `arm`                     |
| `capitalize` | `false` | Uppercase hex bytes and addresses when `true`    |

## Demo

See the `demo/` folder for a complete Hugo site example.

## License

MIT License - see [LICENSE](LICENSE) for details.
