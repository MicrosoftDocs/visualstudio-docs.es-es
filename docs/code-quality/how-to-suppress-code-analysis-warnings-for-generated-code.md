---
title: "C&#243;mo: Suprimir advertencias de an&#225;lisis de c&#243;digo en c&#243;digo generado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# C&#243;mo: Suprimir advertencias de an&#225;lisis de c&#243;digo en c&#243;digo generado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los compiladores del código administrado generan a menudo código que se agrega a un proyecto para facilitar el desarrollo rápido del código.  Además, los programadores utilizan a menudo herramientas de otros fabricantes como ayuda para desarrollar rápidamente las aplicaciones.  Estas herramientas también generan código que se agrega al proyecto.  
  
 Quizá desee ver las infracciones de reglas que el análisis de código detecta en el código generado.  Sin embargo, no deseará verlas si no puede cambiar y mantener el código que contiene la infracción.  
  
 La casilla **Suprimir resultados del código generado** en la página de propiedades Análisis de código de un proyecto le permite seleccionar si desea ver las advertencias de análisis de código referentes al código generado por una herramienta de otro fabricante.  
  
> [!NOTE]
>  Esta opción no suprime los errores y las advertencias del análisis de código generado cuando los errores y advertencias aparecen en formularios y plantillas.  Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
### Para suprimir las advertencias acerca del código generado de un proyecto  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  Haga clic en **Análisis de código**.  
  
3.  Active la casilla **Suprimir resultados del código generado**.