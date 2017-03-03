# Respuestas

1. Escriban qué esperan de cada uno de los pasos

1. Pre-procesador: que pegue el código correspondiente al include (en este caso calculator.h y sus includes) en el código postprocesado.
2. Compilación I: que traduzca el código en C en código assembler
3. Compilación II: que a partir del código assembler genere un objeto en lenguaje de máquina
4. Linkeo: que a partir del lenguaje de máquina genere un ejecutable

2. ¿Qué agregó el preprocesador?

Agregó código (alrededor de 840 líneas) al código C. 

3. Identificar en la rutina de assembler las funciones

	mov	DWORD PTR [rbp-20], edi
	mov	QWORD PTR [rbp-32], rsi
	mov	esi, 11
	mov	edi, 31
	call	add_numbers
	mov	DWORD PTR [rbp-4], eax
	mov	eax, DWORD PTR [rbp-4]
	mov	esi, eax
	mov	edi, OFFSET FLAT:.LC0
	mov	eax, 0
	call	printf

Se ven las funciones add_numbers (con sus argumentos definidos previamente, en esi y edi) y la printf (con su argumento definido previamente en edi, estando la string guardada en .LC0)

4. Explicar qué quieren decir los símbolos que se crean en el objeto

000000000000003c T add_numbers
0000000000000000 T main
                 U printf

T mayúscula quiere decir texto (son funciones definidas, accesibles desde afuera). U quiere decir undefined (printf no está definido en este objeto).

5. ¿En qué se diferencian los símbolos del objeto y del ejecutable?

Aparecen símbolos nuevos en el ejecutable y la printf se encuentra linkeada a la libc, ya que ahora aparece como:

                 U printf@@GLIBC_2.2.5
