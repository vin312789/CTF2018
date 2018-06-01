C語言程式
```
#include <stdio.h>



int main()

{

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
gcc -c hello.s -o hello.o
```
##　連結過程
```
gcc hello.o -o hello
```
