---
title: Calcular métricas del código
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f989e5ec028f3a296585c54eb17b54f4da7c1cf0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917732"
---
# <a name="code-metrics-values"></a>Valores de las métricas de código

La mayor complejidad de las aplicaciones de software moderno también aumenta la dificultad de hacer que el código confiable y fácil de mantener. Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando. Aprovechando las ventajas de las métricas del código, los desarrolladores pueden entender qué tipos o métodos deberían rehacerse o más pruebas. Los equipos de desarrollo pueden identificar los posibles riesgos, comprender el estado actual de un proyecto y realizar un seguimiento del progreso durante el desarrollo de software.

Los desarrolladores pueden usar Visual Studio para generar datos de métricas de código que medir la complejidad y el mantenimiento del código administrado. Datos de métricas de código pueden generarse para una solución completa o un proyecto único.

Para obtener información sobre cómo generar datos de métricas de código en Visual Studio, vea [Cómo: Generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medidas de software

En la lista siguiente se muestra el código de los resultados de las métricas que se calcula de Visual Studio:

- **Índice de mantenimiento** -calcula un valor de índice entre 0 y 100 que representa su relativa facilidad de mantenimiento del código. Un valor alto significa mayor facilidad de mantenimiento. Las clasificaciones de colores, pueden utilizarse para identificar rápidamente los puntos conflictivos en el código. Una clasificación en verde entre 20 y 100 e indica que el código tiene buen mantenimiento. Una calificación amarilla es entre 10 y 19 e indica que el código es moderadamente fácil de mantener. Una clasificación de color rojo es una clasificación entre 0 y 9 e indica un mantenimiento baja.

- **Complejidad ciclomática** -mide la complejidad del código estructural. Se crea, calculando el número de rutas de acceso de código diferente en el flujo del programa. Un programa que tiene el flujo de control complejo requerirá más pruebas para lograr una buena cobertura de código y será más difícil de mantener.

- **Profundidad de herencia** -indica el número de definiciones de clase que se extienden a la raíz de la jerarquía de clases. La profundidad la jerarquía más difícil comprender donde se definen los campos y métodos determinados podría ser o / y ha vuelto a definir.

- **Acoplamiento de clases** -mide el acoplamiento a las clases únicas a través de parámetros, variables locales, tipos de valor devuelto, llamadas a métodos, las creaciones de instancias genérica o de plantilla, clases base, implementaciones de interfaz, los campos definidos en los tipos externos, y decoración de atributo. Buen diseño de software dicta que deben tener alta cohesión y acoplamiento bajo los tipos y métodos. El significativo acoplamiento indica un diseño que es difícil reutilizar y mantener debido a sus interdependencias en otros tipos.

- **Líneas de código** -indica el número aproximado de líneas del código. El recuento se basa en el código IL y, por tanto, no es el número exacto de líneas en el archivo de código fuente. Un número muy alto podría indicar que un tipo o método está intentando hacer demasiado trabajo y debe dividirse. También podría indicar que el tipo o método podría ser difícil de mantener.

   > [!NOTE]
   > El [versión de línea de comandos](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) del código herramienta métricas recuentos reales líneas de código ya que analiza el código fuente en lugar de IL.

## <a name="anonymous-methods"></a>Métodos anónimos

Un *método anónimo* es simplemente un método que no tiene nombre. Métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como parámetro delegado. Resultados de métricas para un método anónimo que se declara en un miembro, como un método o el descriptor de acceso, se asocian con el miembro que declara el método. No se asocian con el miembro que llama al método.

Para obtener más información acerca de cómo tratan las métricas de código los métodos anónimos, consulte [métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Código generado

Algunas herramientas de software y los compiladores generan código que se agrega a un proyecto y que el programador del proyecto no ve o no debe cambiar. Principalmente, las métricas del código omite el código generado cuando calcula los valores de métricas. Esto permite que los valores de las métricas reflejar lo que el desarrollador puede ver y cambiar.

No se omite el código generado para Windows Forms, porque es código que el desarrollador puede ver y cambiar.

## <a name="next-steps"></a>Pasos siguientes

- [Cómo: Generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilice la ventana de resultados de las métricas de código](../code-quality/working-with-code-metrics-data.md)