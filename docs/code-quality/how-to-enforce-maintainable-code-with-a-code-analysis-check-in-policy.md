---
title: "C&#243;mo: Exigir c&#243;digo mantenible con una directiva de protecci&#243;n de los an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código, directivas de protección"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# C&#243;mo: Exigir c&#243;digo mantenible con una directiva de protecci&#243;n de los an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los desarrolladores pueden utilizar la herramienta Métrica del código para medir la complejidad y la facilidad de mantenimiento del código, pero no pueden invocar métricas de código como parte de una directiva de protección.  Sin embargo, un equipo puede habilitar reglas de análisis de código que comprueben la conformidad del código con los estándares de métrica del código y aplicar las reglas mediante directivas de protección.  Para obtener más información sobre las métricas de código, vea [Valores de métrica de código](../code-quality/code-metrics-values.md).  
  
 Los desarrolladores pueden habilitar las reglas de Profundidad de herencia, Acoplamiento de clases, Índice de mantenimiento y Complejidad para aplicar código mantenible a través de las directivas de protección de los análisis de código.  Estas cuatro reglas se encuentran en la categoría "Reglas de mantenimiento" del editor de directiva de análisis de código.  
  
 Los administradores de control de versiones de [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] pueden agregar reglas de mantenimiento de análisis de código a los requisitos de las directivas de protección.  Estas directivas de protección requieren que los desarrolladores ejecuten un análisis de código basado en estos cambios de reglas antes de iniciar la protección.  
  
### Para abrir el editor de directiva de análisis de código  
  
1.  En **Team Explorer**, haga clic con el botón secundario en el proyecto de equipo, seleccione **Configuración del proyecto de equipo** y, a continuación, haga clic en **Control de código fuente**.  
  
     Aparece el cuadro de diálogo **Control de código fuente**.  
  
2.  Haga clic en la pestaña **Directiva de protección** y, a continuación, en **Agregar**.  
  
     Aparecerá el cuadro de diálogo **Agregar directiva de protección**.  
  
3.  En la lista **Directiva de protección**, active la casilla **Análisis de código** y, a continuación, haga clic en **Aceptar**.  
  
     Aparece el cuadro de diálogo **Editor de directiva de análisis de código**.  
  
### Para habilitar las reglas de mantenimiento de análisis de código  
  
1.  En el cuadro de diálogo **Editor de directiva de análisis de código**, bajo **Configuración de reglas**, expanda el nodo **Reglas de mantenimiento**.  
  
2.  Active las casillas para las reglas siguientes:  
  
    -   Profundidad de Herencia: **CA1501 AvoidExcessiveInheritance**. Umbral: advertencia por encima de 5 niveles de profundidad  
  
    -   Complejidad: **CA1502 AvoidExcessiveComplexity**. Umbral: advertencia por encima de 25  
  
    -   Índice de mantenimiento: **CA1505 AvoidUnmaintainableCode**. Umbral: advertencia por debajo de 20  
  
    -   Acoplamiento de clases: **CA1506 AvoidExcessiveClassCoupling**. Umbral: advertencia por encima de 80 para una clase y de 30 para un método  
  
    -   Además, si desea impedir la compilación mediante una infracción de regla, active la casilla **Tratar advertencia como un error** situada junto a la descripción de la regla.  
  
3.  Haga clic en **Aceptar**.  Ahora la nueva directiva de protección se aplicará a las protecciones futuras.  
  
## Vea también  
 [Valores de métrica de código](../code-quality/code-metrics-values.md)   
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)