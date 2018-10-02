---
title: 'Cómo: exigir código mantenible con una directiva de protección de análisis de código | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97b321fe5a72c6f3ace680476340eca48f7ed309
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579975"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: Exigir código mantenible con una directiva de protección de los análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: exigir código mantenible con una directiva de protección de análisis de código](https://docs.microsoft.com/visualstudio/code-quality/how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy).  
  
Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento de su código, pero las métricas del código no pueden invocar como parte de una directiva de protección. Sin embargo, un equipo puede habilitar las reglas de análisis de código que comprueban el cumplimiento de su código con los estándares de las métricas del código y aplican las reglas mediante las directivas de protección. Para obtener más información acerca de las métricas de código, vea el [valores de las métricas de código](../code-quality/code-metrics-values.md).  
  
 Los programadores pueden habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de directivas de protección de análisis de código. Cuatro de estas reglas se encuentra en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.  
  
 Los administradores de la versión de control para [!INCLUDE[esprfound](../includes/esprfound-md.md)] puede agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren que los desarrolladores ejecutar análisis de código en función de estos cambios en las reglas antes de iniciar una inserción en el.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el Editor de directivas de análisis de código  
  
1.  En **Team Explorer**, haga clic en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.  
  
     El **Control de código fuente** aparece el cuadro de diálogo.  
  
2.  En el **directiva de protección** ficha y haga clic en **agregar**.  
  
     El **Agregar directiva de protección** aparece el cuadro de diálogo.  
  
3.  En el **directiva de protección** lista, seleccione el **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.  
  
     El **Editor de directiva de análisis de código** aparece el cuadro de diálogo.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código  
  
1.  En el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de la regla**, expanda el **reglas de mantenimiento** nodo.  
  
2.  Seleccione las casillas de las reglas siguientes:  
  
    -   Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: advertencia en más de 5 niveles de profundidad  
  
    -   Complejidad: **AvoidExcessiveComplexity CA1502** -umbral: advertencia en más de 25  
  
    -   Índice de mantenimiento: **AvoidUnmaintainableCode CA1505** -umbral: advertencia a menos de 20  
  
    -   El acoplamiento de clases: **AvoidExcessiveClassCoupling CA1506** -umbral: advertencia en más de 80 para una clase y más de 30 para un método  
  
    -   Además, si desea que una infracción de regla para evitar que una compilación, seleccione el **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.  
  
3.  Haga clic en **Aceptar**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.  
  
## <a name="see-also"></a>Vea también  
 [Valores de las métricas de código](../code-quality/code-metrics-values.md)   
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



