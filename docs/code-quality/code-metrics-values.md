---
title: Calcular métricas de código en Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3d0bf9b0bf689be847e7f16f2ee01db6e3df6d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919070"
---
# <a name="code-metrics-values"></a>Valores de métrica de código

La mayor complejidad de las aplicaciones de software modernas también aumenta la dificultad de hacer que el código de confianza y fácil de mantener. Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando. Aprovechando las ventajas de las métricas de código, los desarrolladores pueden entender qué tipos y métodos se deben rehacer o probar más a fondo. Los equipos de desarrollo pueden identificar los posibles riesgos, comprender el estado actual de un proyecto y realizar un seguimiento del progreso durante el desarrollo de software.

Los programadores pueden usar Visual Studio para generar datos de métricas de código que medir la complejidad y el mantenimiento del código administrado. Datos de métricas de código se pueden generar para una solución completa o un proyecto único.

Para obtener información sobre cómo generar datos de métricas de código en Visual Studio, vea [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medidas de software

En la lista siguiente muestra el código de los resultados de las métricas que calcula Visual Studio:

- **Índice de mantenimiento** -calcula un valor de índice entre 0 y 100 que representa la facilidad relativa de mantenimiento del código. Un valor alto significa mayor facilidad de mantenimiento. Las clasificaciones de colores, pueden utilizarse para identificar rápidamente los puntos conflictivos en el código. Una clasificación en verde está comprendido entre 20 y 100 e indica que el código tiene buen mantenimiento. Una clasificación amarilla entre 10 y 19 e indica que el código sea fácil de mantener cierta. Una clasificación de color rojo es una clasificación entre 0 y 9 e indica mantenimiento bajo.

- **Complejidad ciclomática** -mide la complejidad estructural del código. Se crea calculando el número de rutas de acceso de código diferentes en el flujo del programa. Un programa que tiene el flujo de control complejo requerirá más pruebas para lograr una buena cobertura de código y será más difícil de mantener.

- **Profundidad de herencia** -indica el número de definiciones de clase que se extiende a la raíz de la jerarquía de clases. La profundidad la jerarquía más difícil puede ser entender donde se definen los campos y métodos determinados o / y ha vuelto a definir.

- **El acoplamiento de clase** -mide el acoplamiento para las clases únicas a través de parámetros, variables locales, tipos de valor devuelto, llamadas a métodos, creaciones de instancias genérica o de plantilla, clases base, implementaciones de interfaz, los campos definidos en los tipos externos, y decoración de atributo. Buen diseño de software indica que los tipos y métodos deben tener cohesión alta y acoplamiento bajo. Un acoplamiento alto indica un diseño que resulta difícil reutilizar y mantener debido a sus interdependencias en otros tipos.

- **Líneas de código** -indica el número aproximado de líneas en el código. El número se basa en el código IL y, por tanto, no es el número exacto de líneas en el archivo de código fuente. Un número muy alto podría indicar que un tipo o método intenta hacer demasiado trabajo y debe dividirse. También puede indicar que el tipo o método podría ser difícil de mantener.

## <a name="anonymous-methods"></a>Métodos anónimos

Un *método anónimo* es simplemente un método que no tiene ningún nombre. Métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como un parámetro de delegado. Resultados de métricas para un método anónimo que se declara en un miembro, como un método o descriptor de acceso, se asocian al miembro que declara el método. No están asociados con el miembro que llama al método.

Para obtener más información acerca de cómo tratan las métricas de código métodos anónimos, vea [métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Código generado

Algunas herramientas de software y los compiladores generan código que se agrega a un proyecto y que el programador del proyecto no ve o no debe cambiar. Principalmente, las métricas de código omiten el código generado al calcular los valores de métricas. Esto permite que los valores de las métricas para que refleje lo que el programador puede ver y cambiar.

No se omite el código generado para formularios Windows Forms, porque es código que el programador puede ver y cambiar.

## <a name="next-steps"></a>Pasos siguientes

- [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilice la ventana de resultados de métrica del código](../code-quality/working-with-code-metrics-data.md)