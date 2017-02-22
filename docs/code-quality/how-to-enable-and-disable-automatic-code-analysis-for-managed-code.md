---
title: "C&#243;mo: Habilitar y deshabilitar el an&#225;lisis de c&#243;digo autom&#225;tico para c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Habilitar y deshabilitar el an&#225;lisis de c&#243;digo autom&#225;tico para c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede configurar el análisis de código para que se ejecute antes de cada compilación de un proyecto de código administrado.  Puede establecer diferentes propiedades de análisis de código para cada configuración de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
### Para habilitar o deshabilitar el análisis de código automático  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  En el cuadro de diálogo de propiedades del proyecto, haga clic en **Análisis de código**.  
  
3.  Especifique el tipo de compilación en **Configuración** y la plataforma de destino en **Plataforma**.  
  
4.  Para habilitar o deshabilitar el análisis de código automático, active o desactive la casilla **Habilitar análisis de código al compilar \(define la constante CODE\_ANALYSIS\)**.