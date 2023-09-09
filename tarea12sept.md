# Common Weakness Enumeration Framework y los CERT Secure Coding Standards

## Similitudes existentes entre ambos

- Tanto el Common Weakness Enumeration Framework como los CERT Secure Coding Standards se enfocan en la seguridad del software y buscan prevenir vulnerabilidades en el mismo.
- Ambos son proyectos comunitarios y están disponibles públicamente para su uso y consulta.
- Los dos se utilizan como guías para desarrolladores y organizaciones que buscan mejorar la seguridad de su software.

## Ejemplos de estándares del CERT que corresponden a un CWE

### CWE-20: Improper Input Validation

#### CERT Secure Coding Standard: STR30-C. Do not attempt to validate the syntax of input using a regular expression

```
c
char input[BUFSIZE];
if (fgets(input, BUFSIZE, stdin) == NULL) {
  /* Handle error */
}
if (strlen(input) > 0 && input[strlen(input)-1] == '\n') {
  input[strlen(input)-1] = '\0';
}
if (strlen(input) != 10) {
  /* Handle error */
}
```

### CWE-78: Improper Neutralization of Special Elements used in an OS Command
#### CERT Secure Coding Standard: IDS00-J. Prevent command injection

```
java
Runtime rt = Runtime.getRuntime();
Process proc = rt.exec("command " + args[0]);
```

### CWE-416: Use After Free
#### CERT Secure Coding Standard: MEM04-C. Be aware of the lifetime of objects

```
void func() {
  int *ptr = (int *)malloc(sizeof(int));
  free(ptr);
  *ptr = 5; /* Use after free */
}
```


## Justificación de los ejemplos con código

En los siguientes ejemplos, se presenta la justificación de cómo los estándares del CERT Secure Coding Standard se relacionan con las vulnerabilidades identificadas por el Common Weakness Enumeration Framework (CWE).

### CWE-20: Improper Input Validation

- **Estándar CERT Secure Coding (STR30-C):** El estándar STR30-C del CERT Secure Coding Standard establece que no se debe intentar validar la sintaxis de la entrada utilizando una expresión regular. En el código proporcionado, se utiliza la función `strlen()` para validar la longitud de la entrada, lo cual no es suficiente para garantizar que la entrada sea válida. Si la entrada no tiene exactamente 10 caracteres, se produce un error. Sin embargo, esto no garantiza que la entrada sea segura y no contenga caracteres maliciosos. Por lo tanto, este código no cumple con el estándar STR30-C.

### CWE-78: Improper Neutralization of Special Elements used in an OS Command

- **Estándar CERT Secure Coding (IDS00-J):** El estándar IDS00-J del CERT Secure Coding Standard establece que se debe evitar la inyección de comandos. En el código proporcionado, se utiliza la entrada del usuario para construir un comando que se ejecuta en el sistema operativo. Esto puede permitir que un atacante inyecte comandos maliciosos en el sistema. Por lo tanto, este código no cumple con el estándar IDS00-J.

### CWE-416: Use After Free

- **Estándar CERT Secure Coding (MEM04-C):** El estándar MEM04-C del CERT Secure Coding Standard establece que se debe tener en cuenta el tiempo de vida de los objetos. En el código proporcionado, se asigna memoria dinámicamente utilizando `malloc()`, pero luego se libera la memoria utilizando `free()`. Sin embargo, después de liberar la memoria, se intenta acceder a la misma utilizando el puntero `ptr`. Esto puede provocar un comportamiento indefinido en el programa y posiblemente una vulnerabilidad de seguridad. Por lo tanto, este código no cumple con el estándar MEM04-C.

En resumen, tanto el Common Weakness Enumeration Framework como los CERT Secure Coding Standards son herramientas importantes para mejorar la seguridad del software. Los ejemplos proporcionados muestran cómo los estándares del CERT pueden ayudar a abordar las vulnerabilidades identificadas por el CWE.



### Referencias
    SEI Digital Library (2019) - MITRE, CWE, and CERT Secure Coding Standards.

    Wikipedia (2021) - Common Weakness Enumeration.

    MITRE (s.f.) - CWE-871: CERT C++ Secure Coding Section 03 - Expressions (EXP) (4.12).

    LinkedIn Learning (2021) - Common Weakness Enumeration (CWE) - CSSLP Cert Prep: 4 Secure Software Implementation Video Tutorial.

    Crashtest Security (2022) - Common Weakness Enumeration Definition and Examples.

    MITRE (2021) - Common Weakness Enumeration: CWE.
