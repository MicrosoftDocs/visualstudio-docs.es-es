---
title: 'Métricas de código: acoplamiento de clases'
ms.date: 1/8/2021
description: Obtenga información sobre la métrica de acoplamiento de clases para las métricas de código Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666814"
---
# <a name="code-metrics---class-coupling"></a>Métricas de código: acoplamiento de clases

El acoplamiento de clases también lleva el nombre Acoplamiento entre objetos (CBO) tal y como se definió originalmente en [CK94.](#ck94) Básicamente, el acoplamiento de clases es una medida de cuántas clases usa una sola clase. Un número alto es malo y un número bajo suele ser bueno con esta métrica. Se ha demostrado que el acoplamiento de clases es una predicción precisa de errores de software y los estudios recientes han demostrado que un valor de límite superior de 9 es el [S2010](#s2010)más eficaz.

Según la documentación de Microsoft, el acoplamiento de clases "mide el acoplamiento a clases únicas a través de parámetros, variables locales, tipos de valor devuelto, llamadas a métodos, instancias genéricas o de plantilla, clases base, implementaciones de interfaz, campos definidos en tipos externos y decoración de atributos. Un buen diseño de software dicta que los tipos y métodos deben tener una grancoherencia y un acoplamiento bajo. El acoplamiento alto indica un diseño difícil de reutilizar y mantener debido a sus numerosas interdependencias con otros tipos".

Los conceptos de acoplamiento ycoherencia están claramente relacionados. Para mantener esta discusión sobre el tema, no entraremos en profundidad con más profundidad que para proporcionar una breve definición de [LALS2000:](#kkls2000)

"Thedone y Constantine introdujeron lacoherencia del módulo como "lo estrechamente enlazados o relacionados entre sí los elementos internos de un módulo" [YC79](#yc79). Un módulo tiene una gran incoherencia si representa exactamente una tarea [...], y todos sus elementos contribuyen a esta única tarea. Describen lacoherencia como un atributo de diseño, en lugar de código, y un atributo que se puede usar para predecir la reusabilidad, el mantenimiento y la capacidad de cambio".

## <a name="class-coupling-example"></a>Ejemplo de acoplamiento de clases

Echemos un vistazo al acoplamiento de clases en acción. En primer lugar, cree una nueva aplicación de consola y una nueva clase denominada Person con algunas propiedades y, a continuación, calcule inmediatamente las métricas de código:

![Ejemplo 1 de acoplamiento de clases](media/class-coupling-example-1.png)

Observe que el acoplamiento de clases es 0, ya que esta clase no usa ninguna otra clase. Ahora cree otra clase denominada PersonStuff con un método que cree una instancia de Person y establece los valores de propiedad. Vuelva a calcular las métricas de código:

![Ejemplo de acoplamiento de clases 2](media/class-coupling-example-2.png)

¿Ve cómo sube el valor de acoplamiento de clase? Observe también que, independientemente del número de propiedades que establezca, el valor de acoplamiento de clase solo sube en 1 y no en ningún otro valor. El acoplamiento de clases mide cada clase solo una vez para esta métrica, independientemente de cuánto se utilice. Además, ¿puede ver que `DoSomething()` tiene un 1, pero el constructor, , tiene un `PersonStuff()` 0 para su valor? Actualmente no hay ningún código en el constructor que use otra clase.

¿Qué ocurre si coloca código en el constructor que usó otra clase? Esto es lo que obtiene:

![Ejemplo 3 de acoplamiento de clases](media/class-coupling-example-3.png)

Ahora el constructor tiene claramente código que usa otra clase y la métrica de acoplamiento de clase muestra este hecho. De nuevo, puede ver que el acoplamiento de clase general para es 1 y también es 1 para mostrar que solo se usa una clase externa independientemente de la cantidad de código interno que tenga que la `PersonStuff()` `DoSomething()` use.

A continuación, cree otra clase. Asigne un nombre a esta clase y cree algunas propiedades dentro de ella:

![Ejemplo de acoplamiento de clases: agregar nueva clase](media/class-coupling-example-add-new-class.png)

Ahora consuma la clase en nuestro `DoSomething()` método dentro de la clase y vuelva a calcular las `PersonStuff` métricas de código:

![Ejemplo 4 de acoplamiento de clases](media/class-coupling-example-4.png)

Como puede ver, el acoplamiento de clases para la clase PersonStuff sube a 2 y, si se profundizar en la clase, puede ver que el método tiene el mayor acoplamiento, pero el constructor sigue consumiendo `DoSomething()` solo 1 clase.  Con estas métricas, puede ver el número máximo total de una clase determinada y explorar en profundidad los detalles por miembro.

## <a name="the-magic-number"></a>Número mágico

Al igual que con la complejidad temática, no hay ningún límite que se ajuste a todas las organizaciones. Sin embargo, [S2010](#s2010) indica que un límite de 9 es óptimo:

"Por lo tanto, consideramos los valores de umbral [...] como el más eficaz. Estos valores de umbral (para un solo miembro) son CBO = 9[...]". (se ha agregado énfasis)

## <a name="code-analysis"></a>Análisis de código

El análisis de código incluye una categoría de reglas de mantenimiento. Para obtener más información, vea [Reglas de mantenimiento.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Cuando se usa el análisis de código heredado, el conjunto de reglas de directriz de diseño extendido contiene un área de mantenimiento:

![Reglas de directriz de diseño extendido de acoplamiento de clases](media/class-coupling-extended-design-guideline-rules.png)

Dentro del área de mantenimiento hay una regla para el acoplamiento de clases:

![Regla de acoplamiento de clases](media/class-coupling-maintainability-area-rules.png)

Esta regla emite una advertencia cuando el acoplamiento de clase es excesivo. Para obtener más información, vea [CA1506: Evitar el acoplamiento excesivo de clases.](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

## <a name="citations"></a>Citas

### <a name="ck94"></a>CK94

Chidagada, S. R. & Kemerer, C. F. (1994). Conjunto de métricas para el diseño orientado a objetos (transacciones IEEE en ingeniería de software, Vol. 20, No. 6). Recuperado el 14 de mayo de 2011 del sitio web de la Universidad de York: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>LS2000

Kabaili, H., Keller, R., Lustman, F. y Saint-Deili, G. (2000). Class Revisited: An Empirical Study on Industrial Systems (Class Revisited: An Empirical Study on Industrial Systems) (Class Revisited: An Empirical Study on Industrial Systems (Procedimientos del Taller sobre enfoques cuantitativos en Object-Oriented ingeniería de software). Recuperado el 20 de mayo de 2011, del sitio web De Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramónm, R. & Hanan, M. S. (2003). Análisis empírico de métricas de CK para la complejidad del diseño de Object-Oriented: implicaciones para defectos de software (transacciones IEEE en ingeniería de software, Vol. 29, No. 4). Recuperado el 14 de mayo de 2011 del sitio web de la Universidad de Massachussets [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Una investigación cuantitativa de los niveles de riesgo aceptables de Object-Oriented métricas en Open-Source Systems (IEEE Transactions on Software Engineering, Vol. 36, No. 2).

### <a name="yc79"></a>YC79

Edward Yourdone y Larry L. Constantine. Diseño estructurado. Prentice Hall, Englewood Cliffs, N.J., 1979.