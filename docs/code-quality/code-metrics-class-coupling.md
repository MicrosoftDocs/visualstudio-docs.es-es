---
title: 'Métricas de código: acoplamiento de clases'
ms.date: 1/8/2021
description: Obtenga información sobre la métrica de acoplamiento de clases para las métricas de código en Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db1308843cb3c4fe8fb0a4aa32300e545e5e3a7c
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069570"
---
# <a name="code-metrics---class-coupling"></a>Métricas de código: acoplamiento de clases

El acoplamiento de clases también pasa por el nombre que se asocia entre los objetos (CBO), como se definió originalmente con [CK94](#ck94). Básicamente, el acoplamiento de clases es una medida del número de clases que usa una sola clase. Un número alto es incorrecto y un número bajo suele ser bueno con esta métrica. Se ha demostrado que el acoplamiento de clases es un predicción preciso de errores de software y los estudios recientes han demostrado que un valor de límite superior de 9 es el [S2010](#s2010)más eficaz.

Según la documentación de Microsoft, el acoplamiento de clases "mide el acoplamiento a clases únicas a través de parámetros, variables locales, tipos de valor devueltos, llamadas a métodos, instancias genéricas o de plantilla, clases base, implementaciones de interfaz, campos definidos en tipos externos y decoración de atributos. Un buen diseño de software dicta que los tipos y métodos deben tener una cohesión alta y un acoplamiento bajo. Un acoplamiento alto indica un diseño que es difícil de reutilizar y mantener debido a sus muchas interdependencias en otros tipos ".

Los conceptos de acoplamiento y cohesión están claramente relacionados. Para mantener este debate en el tema, no profundizaremos con la cohesión que no es ofrecer una breve definición de [KKLS2000](#kkls2000):

"La cohesión de módulos fue introducida por Yourdon y Constantine como" cómo enlazar estrechamente los elementos internos de un módulo entre sí " [YC79](#yc79). Un módulo tiene una cohesión fuerte si representa exactamente una tarea [...], y todos sus elementos contribuyen a esta única tarea. Describen la cohesión como un atributo de diseño, en lugar de código, y un atributo que se puede usar para predecir la reusabilidad, el mantenimiento y la modificación ".

## <a name="class-coupling-example"></a>Ejemplo de acoplamiento de clases

Echemos un vistazo al acoplamiento de clases en acción. En primer lugar, cree una nueva aplicación de consola y cree una nueva clase denominada person con algunas propiedades y, a continuación, calcule inmediatamente las métricas del código:

![Ejemplo 1 de acoplamiento de clases](media/class-coupling-example-1.png)

Observe que el acoplamiento de la clase es 0, ya que esta clase no utiliza otras clases. Ahora cree otra clase llamada PersonStuff con un método que cree una instancia de person y establezca los valores de propiedad. Vuelva a calcular las métricas del código:

![Ejemplo 2 de acoplamiento de clases](media/class-coupling-example-2.png)

¿Ver cómo aumenta el valor de acoplamiento de clase? Observe también que, independientemente del número de propiedades que establezca, el valor de acoplamiento de la clase simplemente aumenta en 1 y no en otro valor. El acoplamiento de clases mide cada clase solo una vez para esta métrica, independientemente de cuánto se use. Además, ¿puede ver que `DoSomething()` tiene un 1, pero el constructor, `PersonStuff()` , tiene un 0 para su valor? Actualmente no hay ningún código en el constructor que use otra clase.

¿Qué ocurre si coloca código en el constructor que usaba otra clase? Esto es lo que obtiene:

![Ejemplo de acoplamiento de clases 3](media/class-coupling-example-3.png)

Ahora el constructor tiene claramente código que utiliza otra clase y la métrica de acoplamiento de clases muestra este hecho. De nuevo, puede ver que el acoplamiento de clases global de `PersonStuff()` es 1 y `DoSomething()` también es 1 para mostrar que solo se usa una clase externa, independientemente de la cantidad de código interno que se utilice.

A continuación, cree otra nueva clase. Asigne a esta clase un nombre y cree algunas propiedades dentro de ella:

![Ejemplo de acoplamiento de clases: agregar nueva clase](media/class-coupling-example-add-new-class.png)

Ahora utilice la clase en nuestro `DoSomething()` método dentro de la `PersonStuff` clase y vuelva a calcular las métricas del código:

![Ejemplo 4 de acoplamiento de clases](media/class-coupling-example-4.png)

Como puede ver, el acoplamiento de clases para la clase PersonStuff alcanza hasta 2 y, si profundiza en la clase, puede ver que el `DoSomething()` método tiene el mayor acoplamiento, pero el constructor todavía solo consume 1 clase.  Con estas métricas, puede ver el número máximo general de una clase determinada y profundizar en los detalles por miembro.

## <a name="the-magic-number"></a>El número mágico

Al igual que con la complejidad ciclomática, no hay ningún límite que se ajuste a todas las organizaciones. Sin embargo, [S2010](#s2010) indica que un límite de 9 es óptimo:

"Por lo tanto, consideramos los valores de umbral [...] como la más eficaz. Estos valores de umbral (para un solo miembro) son CBO = 9 [...]. " (énfasis agregado)

## <a name="code-analysis"></a>Análisis de código

El análisis de código incluye una categoría de reglas de mantenimiento. Para obtener más información, consulte [reglas de mantenimiento](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Al usar el análisis de código heredado, el conjunto de reglas de instrucciones de diseño extendido contiene un área de mantenimiento:

![Reglas de directrices de diseño extendidas de acoplamiento de clases](media/class-coupling-extended-design-guideline-rules.png)

Dentro del área de mantenimiento hay una regla para el acoplamiento de clases:

![Regla de acoplamiento de clases](media/class-coupling-maintainability-area-rules.png)

Esta regla emite una advertencia cuando el acoplamiento de clases es excesivo. Para obtener más información, vea [CA1506: Evite el acoplamiento excesivo de clases](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Para obtener una descripción de esta regla, vea la entrada de blog sobre análisis de código archivado: [métricas de código como Directiva de protección](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) y la advertencia de Descripción del umbral *a las 80 de la clase y por encima de 30 para un método*.  Estos valores parecen anómalomente altos, pero al menos proporcionan un límite superior extremo. Si se alcanza esta advertencia, es casi seguro que algo es incorrecto.

## <a name="citations"></a>Citas

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Un conjunto de métricas para el diseño orientado a objetos (transacciones IEEE en ingeniería de software, Vol. 20, no. 6). Se recuperó el 14 de mayo de 2011 del sitio web de la Universidad de Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F. y Saint-Denis, G (2000). La cohesión de clases se ha revisitado: un estudio empírico sobre sistemas industriales (procedimientos del taller sobre enfoques cuantitativos en Object-Oriented ingeniería de software). Recuperado el 20 de mayo de 2011 del sitio web de Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Análisis empírico de las métricas de CK para la complejidad del diseño de Object-Oriented: implicaciones de defectos de software (transacciones IEEE en ingeniería de software, Vol. 29, no. 4). Recuperado el 14 de mayo de 2011, del sitio web de la Universidad de Massachusetts Dartmouth [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Una investigación cuantitativa de los niveles de riesgo aceptables de Object-Oriented métricas en sistemas Open-Source (transacciones IEEE en ingeniería de software, Vol. 36, no. 2).

### <a name="yc79"></a>YC79

Edward Yourdon y Larry L. Constantine. Diseño estructurado. Prentice Hall, Englewood acantilados, N.J., 1979.