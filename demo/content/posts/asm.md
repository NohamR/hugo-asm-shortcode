---
title: "Adding ASM code blocks"
date: 2026-02-01
summary: "How to add assembly code blocks in Hugo using custom shortcodes"
aliases: ["/posts/asm/"]
tags: ["hugo", "asm", "assembly", "code blocks"]
author: "Noham"
showToc: true
TocOpen: false
draft: true
hidemeta: false
comments: true
disableHLJS: false
disableShare: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
---

### x86 basic example
```go-html-template
{{</* asm mode="raw" arch="x86" */>}}
mov rax, 1
xor rdi, rdi
syscall
{{</* /asm */>}}
```

{{< asm mode="raw" arch="x86" >}}
mov rax, 1
xor rdi, rdi
syscall
{{< /asm >}}

### ARM64 basic example
```go-html-template
{{</* asm mode="raw" arch="arm" */>}}
mov w0, #1
mov w1, #1
add w2, w0, w1
ret
{{</* /asm */>}}
```

{{< asm mode="raw" arch="arm" >}}
mov w0, #1
mov w1, #1
add w2, w0, w1
ret
{{< /asm >}}


### x86 + hex example
```go-html-template
{{</* asm mode="hex" arch="x86" */>}}
48 c7 c0 01 00 00 00 | mov rax, 1
48 31 ff             | xor rdi, rdi
0f 05                | syscall
{{</* /asm */>}}
```

{{< asm mode="hex" arch="x86" >}}
48 c7 c0 01 00 00 00 | mov rax, 1
48 31 ff             | xor rdi, rdi
0f 05                | syscall
{{< /asm >}}

### Hex with capitalization
```go-html-template
{{</* asm mode="hex" capitalize="true" */>}}
48 c7 c0 01 00 00 00 | mov rax, 1
{{</* /asm */>}}
```

{{< asm mode="hex" capitalize="true" >}}
48 c7 c0 01 00 00 00 | mov rax, 1
{{< /asm >}}

### Full example
```go-html-template
{{</* asm mode="full" arch="arm" */>}}
00000000 | 20 00 80 52 | mov w0, #1
00000004 | 21 00 80 52 | mov w1, #1
00000008 | c0 03 5f d6 | ret
{{</* /asm */>}}
```

{{< asm mode="full" arch="arm" >}}
00000000 | 20 00 80 52 | mov w0, #1
00000004 | 21 00 80 52 | mov w1, #1
00000008 | c0 03 5f d6 | ret
{{< /asm >}}

### Full with capitalization
```go-html-template
{{</* asm mode="full" arch="x86" capitalize="true" */>}}
00401000 | 48 c7 c0 01 00 00 00 | mov rax, 1
00401007 | 48 31 ff             | xor rdi, rdi
0040100a | 0f 05                | syscall
{{</* /asm */>}}
```

{{< asm mode="full" arch="x86" capitalize="true" >}}
00401000 | 48 c7 c0 01 00 00 00 | mov rax, 1
00401007 | 48 31 ff             | xor rdi, rdi
0040100a | 0f 05                | syscall
{{< /asm >}}

### ARM64 with hex bytes
```go-html-template
{{</* asm mode="hex" arch="arm" */>}}
20 00 80 52 | mov w0, #1
21 00 80 52 | mov w1, #1
42 00 01 0b | add w2, w2, w1
c0 03 5f d6 | ret
{{</* /asm */>}}
```

{{< asm mode="hex" arch="arm" >}}
20 00 80 52 | mov w0, #1
21 00 80 52 | mov w1, #1
42 00 01 0b | add w2, w2, w1
c0 03 5f d6 | ret
{{< /asm >}}

### Longer x86 function example
```go-html-template
{{</* asm mode="full" arch="x86" */>}}
00401000 | 55                   | push rbp
00401001 | 48 89 e5             | mov rbp, rsp
00401004 | 48 83 ec 10          | sub rsp, 0x10
00401008 | 89 7d fc             | mov [rbp-0x4], edi
0040100b | 8b 45 fc             | mov eax, [rbp-0x4]
0040100e | 83 c0 01             | add eax, 0x1
00401011 | c9                   | leave
00401012 | c3                   | ret
{{</* /asm */>}}
```

{{< asm mode="full" arch="x86" >}}
00401000 | 55                   | push rbp
00401001 | 48 89 e5             | mov rbp, rsp
00401004 | 48 83 ec 10          | sub rsp, 0x10
00401008 | 89 7d fc             | mov [rbp-0x4], edi
0040100b | 8b 45 fc             | mov eax, [rbp-0x4]
0040100e | 83 c0 01             | add eax, 0x1
00401011 | c9                   | leave
00401012 | c3                   | ret
{{< /asm >}}
