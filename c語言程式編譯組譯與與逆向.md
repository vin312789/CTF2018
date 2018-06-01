C語言程式
```
#include <stdio.h>
int main() {
   printf("Hello CTFer\n ");
   return 0;
}
```
## 預處理階段
```
gcc -E hello.c -o hello.i
```
## 編譯階段
```
gcc -S hello.i -o hello.s
```
產生的組合語言
```
	.file	"hello.c"
	.section	.rodata
.LC0:
	.string	"Hello CTFer\n "
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset 6, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register 6
	movl	$.LC0, %edi
	movl	$0, %eax
	call	printf
	movl	$0, %eax
	popq	%rbp
	.cfi_def_cfa 7, 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.5) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```
## 組譯過程
```
gcc-c hello.s -o hello.o
```
使用xxd看看onject file的內容==>xxd hello.o
```
00000000: 7f45 4c46 0201 0100 0000 0000 0000 0000  .ELF............
00000010: 0100 3e00 0100 0000 0000 0000 0000 0000  ..>.............
00000020: 0000 0000 0000 0000 a802 0000 0000 0000  ................
00000030: 0000 0000 4000 0000 0000 4000 0d00 0a00  ....@.....@.....
00000040: 5548 89e5 bf00 0000 00b8 0000 0000 e800  UH..............
00000050: 0000 00b8 0000 0000 5dc3 4865 6c6c 6f20  ........].Hello 
00000060: 4354 4665 720a 2000 0047 4343 3a20 2855  CTFer. ..GCC: (U
00000070: 6275 6e74 7520 352e 342e 302d 3675 6275  buntu 5.4.0-6ubu
00000080: 6e74 7531 7e31 362e 3034 2e35 2920 352e  ntu1~16.04.5) 5.
00000090: 342e 3020 3230 3136 3036 3039 0000 0000  4.0 20160609....
000000a0: 1400 0000 0000 0000 017a 5200 0178 1001  .........zR..x..
000000b0: 1b0c 0708 9001 0000 1c00 0000 1c00 0000  ................
000000c0: 0000 0000 1a00 0000 0041 0e10 8602 430d  .........A....C.
000000d0: 0655 0c07 0800 0000 0000 0000 0000 0000  .U..............
000000e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000000f0: 0100 0000 0400 f1ff 0000 0000 0000 0000  ................
```

##　連結過程
```
gcc hello.o -o hello
```
