---
title: Calcular métricas del código
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886414"
---
# <a name="code-metrics-values"></a>Valores de las métricas de código

La mayor complejidad de las aplicaciones de software moderno también aumenta la dificultad de hacer que el código confiable y fácil de mantener. Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando. Aprovechando las ventajas de las métricas del código, los desarrolladores pueden entender qué tipos o métodos deberían rehacerse o más pruebas. Los equipos de desarrollo pueden identificar los posibles riesgos, comprender el estado actual de un proyecto y realizar un seguimiento del progreso durante el desarrollo de software.

Los desarrolladores pueden usar Visual Studio para generar datos de métricas de código que medir la complejidad y el mantenimiento del código administrado. Datos de métricas de código pueden generarse para una solución completa o un proyecto único.

Para obtener información sobre cómo generar datos de métricas de código en Visual Studio, consulte [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medidas de software

En la lista siguiente se muestra el código de los resultados de las métricas que se calcula de Visual Studio:

- **Índice de mantenimiento** -calcula un valor de índice entre 0 y 100 que representa su relativa facilidad de mantenimiento del código. Un valor alto significa mayor facilidad de mantenimiento. Las clasificaciones de colores, pueden utilizarse para identificar rápidamente los puntos conflictivos en el código. Una clasificación en verde entre 20 y 100 e indica que el código tiene buen mantenimiento. Una calificación amarilla es entre 10 y 19 e indica que el código es moderadamente fácil de mantener. Una clasificación de color rojo es una clasificación entre 0 y 9 e indica un mantenimiento baja. Para obtener más información, consulte la entrada de blog [intervalo de índice de mantenimiento y significado](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) .

- **Complejidad ciclomática** -mide la complejidad del código estructural. Se crea, calculando el número de rutas de acceso de código diferente en el flujo del programa. Un programa que tiene un flujo de control complejo requiere más pruebas para lograr una buena cobertura de código y es menos fácil de mantener. Para obtener más información, consulte la [entrada de Wikipedia para la complejidad ciclomática](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Profundidad de herencia** : indica el número de clases diferentes que heredan de otra, hasta la clase base. La profundidad de la herencia es similar a la Unión de clases en que un cambio en una clase base puede afectar a cualquiera de sus clases heredadas. Cuanto mayor sea este número, más profunda será la herencia y mayor será la posibilidad de que las modificaciones de la clase base produzcan cambios importantes. En cuanto a la profundidad de la herencia, un valor bajo es bueno y un valor alto es incorrecto.

- **Acoplamiento de clases** -mide el acoplamiento a las clases únicas a través de parámetros, variables locales, tipos de valor devuelto, llamadas a métodos, las creaciones de instancias genérica o de plantilla, clases base, implementaciones de interfaz, los campos definidos en los tipos externos, y decoración de atributo. Buen diseño de software dicta que deben tener alta cohesión y acoplamiento bajo los tipos y métodos. El significativo acoplamiento indica un diseño que es difícil reutilizar y mantener debido a sus interdependencias en otros tipos. Para obtener más información, consulte la entrada de blog de [acoplamiento de clases](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Líneas de código fuente** : indica el número exacto de líneas de código fuente que se encuentran en el archivo de código fuente, incluidas las líneas en blanco. Esta métrica está disponible a partir de Visual Studio 2019, versión 16,4 y Microsoft. CodeAnalysis. métricas (2.9.5).

- **Líneas de código ejecutable** : indica el número aproximado de operaciones o líneas de código ejecutable. Se trata de un recuento del número de operaciones en el código ejecutable. Esta métrica está disponible a partir de Visual Studio 2019, versión 16,4 y Microsoft. CodeAnalysis. métricas (2.9.5). Normalmente, el valor es una coincidencia aproximada con la métrica anterior, **líneas de código**, que es la métrica basada en instrucciones de MSIL utilizada en el modo heredado.
::: moniker-end
::: moniker range="vs-2017"

- **Líneas de código** -indica el número aproximado de líneas del código. El recuento se basa en el código IL y, por tanto, no es el número exacto de líneas en el archivo de código fuente. Un recuento alto puede indicar que un tipo o un método está intentando realizar demasiado trabajo y debe dividirse. También podría indicar que el tipo o método podría ser difícil de mantener.

   > [!NOTE]
   > El [versión de línea de comandos](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) del código herramienta métricas recuentos reales líneas de código ya que analiza el código fuente en lugar de IL.
::: moniker-end

## <a name="anonymous-methods"></a>Métodos anónimos

Un *método anónimo* es simplemente un método que no tiene nombre. Métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como parámetro delegado. Los resultados de las métricas de código para un método anónimo que se declara en un miembro, como un método o un descriptor de acceso, están asociados al miembro que declara el método. No se asocian con el miembro que llama al método.

## <a name="generated-code"></a>Código generado

Algunas herramientas de software y los compiladores generan código que se agrega a un proyecto y que el programador del proyecto no ve o no debe cambiar. Principalmente, las métricas del código omite el código generado cuando calcula los valores de métricas. Esto permite que los valores de las métricas reflejar lo que el desarrollador puede ver y cambiar.

No se omite el código generado para Windows Forms, porque es código que el desarrollador puede ver y cambiar.

## <a name="next-steps"></a>Pasos siguientes

- [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilice la ventana de resultados de las métricas de código](../code-quality/working-with-code-metrics-data.md)
