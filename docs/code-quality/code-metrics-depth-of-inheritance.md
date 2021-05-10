---
title: 'Métricas de código: profundidad de herencia'
ms.date: 1/8/2021
description: Obtenga información sobre la profundidad de la métrica de herencia para las métricas de código en Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682607"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Métricas de código: profundidad de herencia (DIT)

En este artículo, aprenderá sobre una de las métricas diseñadas específicamente para el análisis orientado a objetos: Profundidad de herencia. La profundidad de herencia, también denominada profundidad del árbol de herencia (DIT), se define como "la longitud máxima desde el nodo hasta la raíz del [árbol".](#ck) Puede ver esto con un ejemplo sencillo. Cree un nuevo proyecto de biblioteca de clases y, antes de escribir código, calcule las métricas de código eligiendo Analizar > Calcular métricas **de código para la solución**.

![Ejemplo 1 de profundidad de herencia](media/depth-of-inheritance-example-1.png)

Puesto que todas las clases heredan `System.Object` de , la profundidad es 1 actualmente. Si hereda de esta clase y examina la nueva clase, puede ver el resultado:

![Ejemplo 2 de profundidad de herencia](media/depth-of-inheritance-example-2.png)

Observe que cuanto menor sea el nodo del árbol ( en `Class2` este caso), mayor será la profundidad de herencia. Puede continuar con la creación de los secundarios y hacer que la profundidad aumente tanto como desee.

## <a name="assumptions"></a>Suposiciones

La profundidad de la herencia se basa en tres suposiciones fundamentales [CK:](#ck)

1. Cuanto más profunda sea una clase de la jerarquía, mayor será el número de métodos que probablemente herede, lo que dificulta la predicción de su comportamiento.

2. Los árboles más profundos implican una mayor complejidad de diseño, ya que hay más clases y métodos implicados.

3. Las clases más profundas del árbol tienen un mayor potencial para volver a usar métodos heredados.

Las suposiciones 1 y 2 le dicen que tener un número mayor para la profundidad es malo. Si es donde finalizó, estaría en buen estado; sin embargo, la suposición 3 indica que un número mayor de profundidad es bueno para la reutilización potencial del código.

## <a name="analysis"></a>Análisis

Aquí se muestra cómo leer la métrica de profundidad:

- Número bajo de profundidad

  Un número bajo de profundidad implica menos complejidad, pero también la posibilidad de que se reutilice menos código a través de la herencia.

- Número alto de profundidad

  Un número elevado de profundidad implica más posibilidades de reutilización de código a través de la herencia, pero también mayor complejidad con una mayor probabilidad de errores en el código.

## <a name="code-analysis"></a>Análisis de código

El análisis de código incluye una categoría de reglas de mantenimiento. Para obtener más información, vea [Reglas de mantenimiento.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Cuando se usa el análisis de código heredado, el conjunto de reglas de directriz de diseño extendido contiene un área de mantenimiento:

![Profundidad de los conjuntos de reglas de directrices de diseño de herencia](media/depth-of-inheritance-design-guidelines.png)

Dentro del área de mantenimiento hay una regla para la herencia:

![Regla de mantenimiento de profundidad de herencia](media/depth-of-inheritance-maintainability-rule.png)

Esta regla emite una advertencia cuando la profundidad de herencia alcanza 6 o más, por lo que es una buena regla para ayudar a evitar una herencia excesiva. Para obtener más información sobre la regla, vea [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Poner todo juntos

Los valores altos de DIT significan que el potencial de errores también es alto y los valores bajos reducen la posibilidad de errores. Los valores altos de DIT indican un mayor potencial de reutilización de código a través de la herencia; los valores bajos sugieren menos reutilización de código a través de la herencia que se debe aprovechar. Debido a la falta de datos suficientes, no hay ningún estándar aceptado actualmente para los valores de DIT. Incluso los estudios realizados recientemente no han encontrado datos suficientes para determinar un número viable que se pueda usar como un número estándar para esta [métrica Shatnawi](#shatnawi). Aunque no hay ninguna evidencia empírica que lo admita, varios recursos sugieren que un DIT de alrededor de 5 o 6 debe ser un límite superior. Por ejemplo, vea [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) .

## <a name="citations"></a>Citas

### <a name="ck"></a>CK

Chidagada, S. R. & Kemerer, C. F. (1994). Conjunto de métricas para el diseño orientado a objetos (transacciones IEEE en ingeniería de software, Vol. 20, No. 6). Recuperado el 14 de mayo de 2011 del sitio web de la Universidad de York: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramónm, R. & Hanan, M. S. (2003). Análisis empírico de métricas de CK para la complejidad del diseño de Object-Oriented: implicaciones para defectos de software (transacciones IEEE en ingeniería de software, Vol. 29, No. 4). Recuperado el 14 de mayo de 2011, obtenido originalmente del sitio web de la Universidad de Massachussets [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Una investigación cuantitativa de los niveles de riesgo aceptables de Object-Oriented métricas en Open-Source Systems (IEEE Transactions on Software Engineering, Vol. 36, No. 2).