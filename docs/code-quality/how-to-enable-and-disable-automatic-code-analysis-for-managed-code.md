---
title: "Cómo: habilitar y deshabilitar el análisis de código automático para código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 198047196ba6f58c69736ef67352267845047b52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Cómo: Habilitar y deshabilitar el análisis de código automático para código administrado
Puede configurar el análisis de código para que se ejecute antes de cada compilación de un proyecto de código administrado. Puede establecer distintas propiedades de análisis de código para cada [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] configuración.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar o deshabilitar el análisis de código automático  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.  
  
2.  En el cuadro de diálogo de propiedades para el proyecto, haga clic en **análisis de código**.  
  
3.  Especifique el tipo de compilación en **configuración** y la plataforma de destino en **plataforma**.  
  
4.  Para habilitar o deshabilitar el análisis de código automático, active o desactive el **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** casilla de verificación.