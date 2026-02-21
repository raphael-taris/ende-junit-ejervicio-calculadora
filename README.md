# Testing con Junit

Este es un ejemplo sencillo de pruebas unitarias usando Junit 5

Observa que este proyecto no tiene ninguna clase con el método `main`, no nos hace fatal. Además, tampoco tiene ningún `scanner` ni ningún `print`.

Haz un fork de este proyecto en tu repositorio de Github y contesta a las siguientes preguntas:




1. ¿Qué sentido puede tener este proyecto y para que lo podrías usar?


RESPUESTA: En este proyecto queremos enfocarnos solo en que la calculadora haga bien las operaciones matemáticas, sin depender de que alguien escriba datos por teclado o vea resultados en pantalla, pr eso no tenemos 'main', 'scanner' ni 'print'. Así podemos probar automáticamente que todo funciona correctamente.
Este proyecto se podría usar como base para aplicaciones más avanzadas.




2. Revisa las pruebas de la suma y comenta lo que te parezca de interés

RESPUESTA: Lo primero que veo a destacar es que el test sumarPositivosMal() está diseñado intencionadamente para fallar (afirma que 2+3=4).

También el uso de 'assertAll'. En lugar de hacer comprobaciones sueltas, agrupa varias. Así, si una falla, el test sigue ejecutando las demás y da un informe completo.




3. Realiza un estudio de caja negra de la división e implementa las pruebas en junit: Se realizará en markdown.

-Determinar clases de equivalencia:
    Clase Válida: Un entero en el dividendo (a) y un entero distinto de cero en el divisor (b).

    Clase No Válida:  Un entero en el dividendo (a) y el número '0'en el divisor (b).

-Análisis de valores límites:
    Cuando el divisor (b) se acerca a 0 o es exactamente 0.
    
    Usar números muy grandes o muy peqeuños.

-Pruebas aleatorias:
    Introducir valores positivos y negativos aleatorios dentro de las clases de equivalencia válidas (ej. a = -9, b = 3).

-Conjetura de errores:
    Si la división no es exacta -> Al usar 'int' se truncan los decimales. Es un posible punto de fallo si el usuario espera decimales, por lo que lo probamos.
    Si el dividendo es '0' ->  0/ 5 debería dar 0 sin dar error.

-Generar casos de uso para probar las clases válidas y no válidas. Establecer datos de entrada y resultados esperados:
    @Test
    @DisplayName("Probar divisiones válidas según los casos de uso")
    void dividir() throws OperacionNoValidaException {
        assertAll("Casos de uso de la División",
            // Caso 1: División exacta
            () -> assertEquals(2, Calculadora.dividir(10, 5), "10 / 5 = 2"),
            // Caso 2: División truncada
            () -> assertEquals(2, Calculadora.dividir(5, 2), "5 / 2 = 2 (se truncan decimales)"),
            // Caso 3: Negativos
            () -> assertEquals(-3, Calculadora.dividir(-9, 3), "-9 / 3 = -3"),
            // Caso 4: Dividendo cero
            () -> assertEquals(0, Calculadora.dividir(0, 4), "0 / 4 = 0")
        );
    }

## Instrucciones

El alumno deberá hacer un fork de este proyecto e implementar la solución solicitada (preguntas y código).

>Se deberá utilizar este fichero, y los artefactos de código del proyecto, para resolver el ejercicio.


**Si no se puede acceder al repositorio la evaluación del ejercicio será de 0. No se evaluarán entregas modificadas/entregadas fuera del plazo establecido en la tarea**