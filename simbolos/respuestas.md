Los símbolos en el visibility.o son

0000000000000000 t add_abs
000000000000002a T main
                 U printf
0000000000000000 r val1
0000000000000004 R val2
0000000000000000 d val3
0000000000000004 D val4

que en relación al visibility.c, aparecen compilados de la siguiente forma:

static int add_abs: como función accesible desde adentro del programa (t)
int main: accesible desde afuera
printf: como undefined (se linkea luego con la libc)
static const int val1: como readonly accesible desde adentro
const int val2: como readonly accesible desde afuera
static int val3: dato accesible desde adentro
int val4: dato accesible desde afuera
 
