---
title: Valores de las métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667722"
---
# <a name="code-metrics-values"></a>Valores de métrica de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando. Mediante el uso de métricas de código, los desarrolladores pueden comprender qué tipos y métodos deben reasignarse o probarse con más detalle. Los equipos de desarrollo pueden identificar posibles riesgos, comprender el estado actual de un proyecto y realizar un seguimiento del progreso durante el desarrollo de software.

## <a name="software-measurements"></a>Medidas de software
 En la lista siguiente se muestran los resultados de las métricas de código que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] calcula:

- **Índice de mantenimiento** : calcula un valor de índice entre 0 y 100 que representa la facilidad relativa de mantenimiento del código. Un valor alto significa un mejor mantenimiento. Las clasificaciones codificadas por colores se pueden usar para identificar rápidamente los puntos problemáticos en el código. Una clasificación verde está entre 20 y 100 e indica que el código tiene buena capacidad de mantenimiento. Una clasificación amarilla está comprendida entre 10 y 19 e indica que el código se mantiene de forma moderada. Una clasificación de color rojo es una clasificación entre 0 y 9 y indica un mantenimiento bajo.

- **Complejidad ciclomática** : mide la complejidad estructural del código. Se crea calculando el número de rutas de acceso de código diferentes en el flujo del programa. Un programa que tenga un flujo de control complejo requerirá más pruebas para lograr una buena cobertura de código y será menos fácil de mantener.

    > [!NOTE]
    > En algunos casos, el cálculo de la complejidad ciclomática de un método en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] difiere de las versiones anteriores. Para obtener más información, vea la sección "cambios en los cálculos de complejidad de código de Visual Studio 2010" de [solucionar problemas de métricas de código](../code-quality/troubleshooting-code-metrics-issues.md).

- **Profundidad de herencia** : indica el número de definiciones de clase que se extienden a la raíz de la jerarquía de clases. Cuanto más difícil sea la jerarquía, más difícil será entender dónde se definen y/y se redefinen determinados métodos y campos.

- **Acoplamiento de clases** : mide el acoplamiento a clases únicas a través de parámetros, variables locales, tipos de valor devueltos, llamadas a métodos, instancias genéricas o de plantilla, clases base, implementaciones de interfaz, campos definidos en tipos externos y atributo Decora. Un buen diseño de software dicta que los tipos y métodos deben tener una cohesión alta y un acoplamiento bajo. Un acoplamiento alto indica un diseño que es difícil de reutilizar y mantener debido a sus muchas interdependencias en otros tipos.

- **Líneas de código** : indica el número aproximado de líneas en el código. El recuento se basa en el código IL y, por tanto, no es el número exacto de líneas en el archivo de código fuente. Un recuento muy alto puede indicar que un tipo o un método está intentando realizar demasiado trabajo y debe dividirse. También puede indicar que el tipo o el método pueden ser difíciles de mantener.

## <a name="anonymous-methods"></a>Métodos anónimos
 Un *método anónimo* es simplemente un método que no tiene nombre. Los métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como un parámetro de delegado. Los resultados de las métricas para un método anónimo que se declara en un miembro, como un método o un descriptor de acceso, están asociados al miembro que declara el método. No están asociados al miembro que llama al método.

 Para obtener más información sobre cómo trata las métricas de código los métodos anónimos, vea [métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Código generado
 Algunas herramientas y compiladores de software generan código que se agrega a un proyecto y que el desarrollador del proyecto no ve o no debe cambiar. Principalmente, las métricas de código omiten el código generado cuando calcula los valores de las métricas. Esto permite que los valores de las métricas reflejen lo que el desarrollador puede ver y cambiar.

 El código generado para Windows Forms no se pasa por alto porque es código que el desarrollador puede ver y cambiar.

## <a name="see-also"></a>Vea también
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
