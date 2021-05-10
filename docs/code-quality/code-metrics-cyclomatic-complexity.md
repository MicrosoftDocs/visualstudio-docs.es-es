---
title: 'Métricas de código: complejidad deMatic'
ms.date: 5/7/2021
description: Obtenga información sobre la métrica de complejidad temática para las métricas de código en Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682605"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Métricas de código: complejidad deMatic

Al trabajar con métricas de código, uno de los elementos menos comprendidos parece ser una complejidad temática. Básicamente, con complejidad temática, los números más altos son negativos y los números más bajos son buenos. Puede usar la complejidad tómática para obtener una idea de lo difícil que puede ser probar, mantener o solucionar problemas de un código determinado, así como una indicación de la probabilidad de que el código produzca errores. En un nivel alto, determinamos el valor de la complejidad política contando el número de decisiones tomadas en el código fuente. En este artículo, comenzará con un ejemplo sencillo de complejidad temática para comprender el concepto rápidamente y, a continuación, verá información adicional sobre el uso real y los límites sugeridos. Por último, hay una sección de citas que se puede usar para profundizar más en este tema.

## <a name="example"></a>Ejemplo

La complejidad matemática se define como la medición de "la cantidad de lógica de decisión en una función de código fuente" [NIST235](#nist235). En pocas palabras, más decisiones se deben tomar en el código, más complejas son.

Vamos a verlo en acción. Cree una nueva aplicación de consola y calcule inmediatamente las métricas de código; para lo que debe ir a **Analizar > calcular métricas de código para la solución**.

![Ejemplo 1 de complejidad temática](media/cyclomatic-complexity-example-1.png)

Observe que la complejidad temática está en 2 (el valor más bajo posible). Si agrega código que no es de decisión, observe que la complejidad no cambia:

![Ejemplo 2 de complejidad temática](media/cyclomatic-complexity-example-2.png)

Si agrega una decisión, el valor de complejidad temática aumenta en 1:

![Ejemplo 3 de complejidad temática](media/cyclomatic-complexity-example-3.png)

Al cambiar la instrucción if a una instrucción switch con 4 decisiones que se deben tomar, pasa del 2 original al 6:

![Ejemplo 4 de complejidad tecnológica](media/cyclomatic-complexity-example-4.png)

Echemos un vistazo a una base de código (hipotéticamente) mayor.

![Ejemplo 5 de complejidad tecnológica](media/cyclomatic-complexity-example-5.png)

Observe que la mayoría de los elementos, al explorar en profundidad la clase Products_Related, tienen un valor de 1, pero un par de ellos tienen una complejidad de 5. Por sí solo, puede que esto no sea una gran cosa, pero dado que la mayoría de los demás miembros tienen un 1 en la misma clase, definitivamente debería mirar más de cerca esos dos elementos y ver lo que hay en ellos. Para ello, haga clic con el botón derecho en el elemento y elija Ir al código **fuente** en el menú contextual. Echa un vistazo más de cerca a `Product.set(Product)` :

![Ejemplo 6 de complejidad tecnológica](media/cyclomatic-complexity-example-6.png)

Dadas todas las instrucciones if, puede ver por qué la complejidad técnica es de 5. En este momento, puede decidir que se trata de un nivel de complejidad aceptable, o bien puede refactorizar para reducir la complejidad.

## <a name="the-magic-number"></a>Número mágico

Al igual que con muchas métricas de este sector, no hay ningún límite exacto de complejidad de la zona que se ajuste a todas las organizaciones. Sin embargo, [NIST235](#nist235) indica que un límite de 10 es un buen punto de partida:

"El número preciso que se usará como límite, sin embargo, sigue siendo un poco desenlome. El límite original de 10 tal y como lo ha propuesto McCabe tiene evidencias de apoyo significativas, pero también se han usado con éxito límites de hasta 15. Los límites superiores a 10 deben reservarse para los proyectos que tienen varias ventajas operativas con respecto a los proyectos típicos, por ejemplo, personal experimentado, diseño formal, un lenguaje de programación moderno, programación estructurada, tutoriales de código y un plan de prueba completo. En otras palabras, una organización puede elegir un límite de complejidad mayor que 10, pero solo si está seguro de que sabe lo que hace y está dispuesto a dedicar el esfuerzo de prueba adicional que requieren los módulos más complejos." [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Complejidad asómática y números de línea

Simplemente mirar el número de líneas de código por sí mismo es, en el mejor de los casos, un predictor muy amplio de la calidad del código. Hay cierta verdad básica en la idea de que, entre más líneas de código de una función, más probable es tener errores. Sin embargo, al combinar la complejidad tómática con líneas de código, tiene una imagen mucho más clara de la posibilidad de errores.

Como se describe en Software Assurance Technology Center (SATC) de la NASA:

"La SATC ha encontrado que la evaluación más eficaz es una combinación de tamaño y complejidad (Matic). Los módulos con una complejidad alta y un tamaño grande tienden a tener la confiabilidad más baja. Los módulos con un tamaño bajo y una complejidad alta también son un riesgo de confiabilidad porque tienden a ser código muy tenso, lo que es difícil de cambiar o modificar". [SATC](#satc)

## <a name="code-analysis"></a>Análisis de código

El análisis de código incluye una categoría de reglas de mantenimiento. Para obtener más información, vea [Reglas de mantenimiento.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Cuando se usa el análisis de código heredado, el conjunto de reglas de directriz de diseño extendido contiene un área de mantenimiento:

![Conjuntos de reglas de directrices de diseño de complejidad temática](media/cyclomatic-complexity-design-guidelines.png)

Dentro del área de mantenimiento hay una regla para la complejidad:

![Regla de mantenimiento de complejidad temática](media/cyclomatic-complexity-maintainability-rule.png)

Esta regla emite una advertencia cuando la complejidad política alcanza los 25, por lo que puede ayudarle a evitar una complejidad excesiva. Para más información sobre la regla, consulte [CA1502.](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Poner todo juntos

La conclusión es que un número de complejidad alta significa una mayor probabilidad de errores con un mayor tiempo de mantenimiento y solución de problemas. Mire con más atención las funciones que tienen una gran complejidad y decida si se deben refactorizar para que sean menos complejas.

## <a name="citations"></a>Citas

### <a name="mccabe5"></a>MCCABE5

McCabe, T. y A. Watson (1994), Complejidad del software (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Pruebas estructuradas: una metodología de prueba que usa la métrica de complejidad socimática (publicación especial de NIST 500-235). Recuperado el 14 de mayo de 2011 del sitio web de McCabe Software: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Roslk, L., Hammer, T., Hammer, J. (1998). Métricas de software y confiabilidad (Procedimientos del Ieee International Symposium on Software Reliability Engineering). Recuperado el 14 de mayo de 2011, del sitio web de University State State: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)