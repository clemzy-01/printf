ALX FIRST TEAM PROJECT - Printf

_printf

_printf is a custom implementation of the C programming function printf. This project is an application of the C programming knowledge that Holberton School cohort 3 students have learned since starting the program on May 1, 2017.



Prototype: int _printf(const char *, ...);



Examples

String



Input: _printf("%s\n", 'This is a string.');

Output: This is a string.

Character



Input: _printf("The first letter in the alphabet is %c\n", 'A');

Output: The first letter in the alphabet is A

Integer



Input: _printf("There are %i dozens in a gross\n", 12);

Output: There are 12 dozens in a gross

Decimal:



Input: _printf("%d\n", 1000);

Output: 1000

Project Requirements

All files will be compiled on Ubuntu 20.04.1 LTS

Programs and functions will be compiled with gcc 9.4.0 using flags -Wall -Werror -Wextra and -pedantic

Code must follow the Betty style

Global variables are not allowed

Authorized functions and macros:

write (man 2 write)

malloc (man 3 malloc)

free (man 3 free)

va_start (man 3 va_start)

va_end (man 3 va_end)

va_copy (man 3 va_copy)

va_arg (man 3 va_arg)

Mandatory Tasks

 Write function that produces output with conversion specifiers c, s, and %.

 Handle conversion specifiers d, i.

 Create a man page for your function.

Advanced Tasks

 Handle conversion specifier b.

 Handle conversion specifiers u, o, x, X.

 Use a local buffer of 1024 chars in order to call write as little as possible.

 Handle conversion specifier S.

 Handle conversion specifier p.

 Handle flag characters +, space, and # for non-custom conversion specifiers.

 Handle length modifiers l and h for non-custom conversion specifiers.

 Handle the field width for non-custom conversion specifiers.

 Handle the precision for non-custom conversion specifiers.

 Handle the 0 flag character for non-custom conversion specifiers.

 Handle the custom conversion specifier r that prints the reversed string.

 Handle the custom conversion specifier R that prints the rot13'ed string.

 All above options should work well together.



Synopsis

This function _printf() writes output to stdout, the standard output stream with the format and options without making use of any of the standard library files. It was written to use a local buffer of 1024 bytes when printing although it can print larger sets of data.



The _printf() function returns the total number of characters printed to the stdout(excluding the null byte at the end of strings) after a successful execution.



If an output error is encountered, a negative value of -1 is returned.



The prototype of this function is: int _printf(const char format, ...);



This means that it has one mandatory format argument, and an extra number of arguments that can be none, or many.



Format of the format string



The format string is a character string starting and ending with double quotes. The format string is composed of zero or more directives; ordinary characters (not %), and conversion specifications, each of which results in fetching zero or more subsequent arguments.



Each conversion specification is introduced by the character % and ends with a conversion specifier. In between there may be (in this order):



Zero or more flags



An optional field width



An optional precision modifier



An optional length modifier



The flag characters



Flag	Description

#	For o conversions the first character of the output string is made zero (by prefixing a 0 if it was not zero already). For x and X conversions, a nonzero result has the string "0x" or "0X" respectively added.

0	(Not implemented yet) The value should be zero padded. For d, i, o, u, x, and X the converted value is padded on the left with zeros. If the 0 and - flags both appear,the 0 flag is ignored. If a precision is given with a numeric conversion, the 0 flag is ignored.

-	(Minus sign, not implemented yet) The converted value is to be left adjusted on the field boundary, (Default is right justification) and padded with blanks in the right rather than on the left with blanks or zeros. This flag overrides 0 if both are given.

' '	(Blank Space) The argument is padded with a single blank space before a positive number or empty string produced by a signed conversion.

+	A sign (+ or -) should always be placed before a number produced with a signed conversion. By default, only negative numbers have this sign.

The field width



An optional decimal digit string (with nonzero first digit) specifying a minimum field width. If the converted value has fewer characters than the field width, it will be padded with spaces on the left if the flag - is not present, and on the right if it is present. A character * can be used instead of a decimal string. In this case, an argument passed to the function will be taken as the width value.



printf("%5d", num);

or



printf("%*d", width, num);

The precision



An optional precision, in the form of a period ('.') followed by an optional decimal digit string. A negative precision is taken as if the precision were omitted. This gives the minimum number of digits to appear for d, i, o, u, x, and X conversions, or the maximum number of characters to be printed from a string for s and S conversions. A character * can be used instead of a decimal string. In this case, an argument passed to the function will be taken as the precision value.



printf("%.3d", num);

or



printf("%.*d", precision, num);

The length modifiers



Modifier	Description

l	An integer conversion to a long int or unsigned long int argument.

h	An integer conversion to a short int or unsigned short int argument.

The conversion specifier



Specifier	Description

d, i	The argument int is converted to a signed decimal notation. If precision is present,it gives the minimum number of digits that must appear; if the converted value requires fewer digits, then it is padded with zeros on the left. Default precision is 1.

o, u, x, X	The argument is converted to unsigned octal (o), unsigned decimal (u), or unsigned hexamedical (x and X) notation. The letters abcdef are used for x conversion and the letters ABCDEF are used for X conversion. If precision is present, it will give the minimum number of digits that must appear; if the converted value requires fewer digits, then it will be padded with zeros. By default the precision is 1.

c	The int argument is converted to an unsigned char and the resulting character is written. The representation of characters is based off the ASCII coding.

s	The argument received is expected to be a pointer type char * to an array of characters. Characters from this array are printed up to (but not including) a null byte ('\0'). If precision is specified, then this will determine how many characters are taken into account for printing.

p	A void * pointer argument is printed as hexadecimal in lower caps representing an adress in memory.

%	A ' % ' character is written and no conversion is made. The specification is as follows: %%.

b	The argument is converted to an unsigned int value and then operated to get its binary representation (base 2).

S	The argument received is expected to be a pointer type char * to an array of characters. Characters from this array are printed up to (but not including) a null byte ('\0'). Non printable characters (0 < ASCII value < 32 or >= 127) are printed this way: \x, followed by the ASCII code value in hexadecimal (upper case - always 2 characters).

r	The argument received is expected to be a pointer type char * to an array of characters. Characters from this array are printed in reverse order up to (but not including) a null byte ('\0').

R	The argument received is expected to be a pointer type char * to an array of characters. Characters from this array are encoded to ROT13 and printed in order up to (but not including a null byte ('\0').



File Descriptions

_printf.c: - contains the fucntion _printf, which uses the prototype int _printf(const char *format, ...);. The format string is composed of zero or more directives. See man 3 printf for more detail. _printf will return the number of characters printed (excluding the null byte used to end output to strings) and will write output to stdout, the standard output stream.

_putchar.c: - contains the function _putchar, which writes a character to stdout.

holberton.h: - contains all function prototypes used for _printf.

man_3_printf: - manual page for the custom _printf function.

print_chars.c: - contains the functions print_c, print_s, print_S, and print_r which handle the conversion specifiers c, s, S, and r, respectively, as well as hex_print, which prints a char's ascii value in uppercase hex

print_numbers.c: - contains the functions print_i and print_d, which handle the conversion specifiers i and d, respectively

print_hex.c: - contains the functions print_hex, which prints an unsigned int in hexidecimal form, print_x, print_X, and print_p, which handle the conversion specifiers x, X, and p, respectively

print_unsigned_int.c: - contains the functions print_u, print_o, and print_b, which handle the conversion specifiers u, o, and b, respectively

print_rot13.c - contains the function print_R, which handles the conversion specifier R

Authors

Clem Mordi | @clemzy-01

Ella Nsofor | @ella-123nsofor
