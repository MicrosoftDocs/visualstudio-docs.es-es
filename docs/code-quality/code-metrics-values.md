---
title: Calcular métricas de código
ms.date: 11/02/2018
description: Obtenga información sobre la complejidad ciclomática, el acoplamiento de clases y otras métricas de Visual Studio Code. Vea cómo las métricas pueden realizar el seguimiento del progreso del desarrollo e identificar los riesgos.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e77667feae806b66092195f30b028ccca653b2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860456"
---
# <a name="code-metrics-values"></a>Valores de las métricas de código

La mayor complejidad de las aplicaciones de software modernas también aumenta la dificultad de hacer que el código sea confiable y fácil de mantener. Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando. Mediante el uso de métricas de código, los desarrolladores pueden comprender qué tipos y métodos deben reasignarse o probarse con más detalle. Los equipos de desarrollo pueden identificar posibles riesgos, comprender el estado actual de un proyecto y realizar un seguimiento del progreso durante el desarrollo de software.

Los desarrolladores pueden usar Visual Studio para generar datos de métricas de código que midan la complejidad y el mantenimiento de su código administrado. Se pueden generar datos de métricas de código para una solución completa o un único proyecto.

Para obtener información sobre cómo generar datos de métricas de código en Visual Studio, consulte [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medidas de software

En la siguiente lista se muestran los resultados de las métricas de código que calcula Visual Studio:

- **Índice de mantenimiento** : calcula un valor de índice entre 0 y 100 que representa la facilidad relativa de mantenimiento del código. Un valor alto significa un mejor mantenimiento. Las clasificaciones codificadas por colores se pueden usar para identificar rápidamente los puntos problemáticos en el código. Una clasificación verde está entre 20 y 100 e indica que el código tiene buena capacidad de mantenimiento. Una clasificación amarilla está comprendida entre 10 y 19 e indica que el código se mantiene de forma moderada. Una clasificación de color rojo es una clasificación entre 0 y 9 y indica un mantenimiento bajo. Para obtener más información, vea [intervalo del índice de mantenimiento y significado](code-metrics-maintainability-index-range-and-meaning.md).

- **Complejidad ciclomática** : mide la complejidad estructural del código. Se crea calculando el número de rutas de acceso de código diferentes en el flujo del programa. Un programa que tiene un flujo de control complejo requiere más pruebas para lograr una buena cobertura de código y es menos fácil de mantener. Para obtener más información, consulte la [entrada de Wikipedia para la complejidad ciclomática](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Profundidad de herencia** : indica el número de clases diferentes que heredan de otra, hasta la clase base. La profundidad de la herencia es similar a la Unión de clases en que un cambio en una clase base puede afectar a cualquiera de sus clases heredadas. Cuanto mayor sea este número, más profunda será la herencia y mayor será la posibilidad de que las modificaciones de la clase base produzcan cambios importantes. En cuanto a la profundidad de la herencia, un valor bajo es bueno y un valor alto es incorrecto.

- **Acoplamiento de clases** : mide el acoplamiento a clases únicas a través de parámetros, variables locales, tipos de valor devueltos, llamadas a métodos, instancias genéricas o de plantilla, clases base, implementaciones de interfaz, campos definidos en tipos externos y decoración de atributos. Un buen diseño de software dicta que los tipos y métodos deben tener una cohesión alta y un acoplamiento bajo. Un acoplamiento alto indica un diseño que es difícil de reutilizar y mantener debido a sus muchas interdependencias en otros tipos. Para obtener más información, vea [acoplamiento de clases](code-metrics-class-coupling.md).

::: moniker range=">=vs-2019"

- **Líneas de código fuente** : indica el número exacto de líneas de código fuente que se encuentran en el archivo de código fuente, incluidas las líneas en blanco. Esta métrica está disponible a partir de Visual Studio 2019, versión 16,4 y Microsoft. CodeAnalysis. Metrics (2.9.5).

- **Líneas de código ejecutable** : indica el número aproximado de operaciones o líneas de código ejecutable. Se trata de un recuento del número de operaciones en el código ejecutable. Esta métrica está disponible a partir de Visual Studio 2019, versión 16,4 y Microsoft. CodeAnalysis. Metrics (2.9.5). Normalmente, el valor es una coincidencia aproximada con la métrica anterior, **líneas de código**, que es la métrica basada en instrucciones de MSIL utilizada en el modo heredado.
::: moniker-end
::: moniker range="vs-2017"

- **Líneas de código** : indica el número aproximado de líneas en el código. El recuento se basa en el código IL y, por tanto, no es el número exacto de líneas en el archivo de código fuente. Un recuento alto puede indicar que un tipo o un método está intentando realizar demasiado trabajo y debe dividirse. También puede indicar que el tipo o el método pueden ser difíciles de mantener.

   > [!NOTE]
   > La [versión de línea de comandos](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) de la herramienta de métricas de código cuenta las líneas de código reales porque analiza el código fuente en lugar de Il.
::: moniker-end

## <a name="anonymous-methods"></a>Métodos anónimos

Un *método anónimo* es simplemente un método que no tiene nombre. Los métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como un parámetro de delegado. Los resultados de las métricas de código para un método anónimo que se declara en un miembro, como un método o un descriptor de acceso, están asociados al miembro que declara el método. No están asociados al miembro que llama al método.

## <a name="generated-code"></a>Código generado

Algunas herramientas y compiladores de software generan código que se agrega a un proyecto y que el desarrollador del proyecto no ve o no debe cambiar. Principalmente, las métricas de código omiten el código generado cuando calcula los valores de las métricas. Esto permite que los valores de las métricas reflejen lo que el desarrollador puede ver y cambiar.

No se omite el código generado para Windows Forms, porque es código que el desarrollador puede ver y cambiar.

## <a name="next-steps"></a>Pasos siguientes

- [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Usar la ventana Resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)