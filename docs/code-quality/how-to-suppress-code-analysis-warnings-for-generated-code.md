---
title: "Cómo: Suprimir advertencias de análisis de código para el código generado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd917c8c9a3b66dc1fe34e089e14481c2b7df5a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Cómo: Suprimir advertencias de análisis de código en código generado
Compiladores de código administrado a menudo generan código que se agrega a un proyecto para facilitar el desarrollo rápido de código. Además, los desarrolladores suelen usar herramientas de otros fabricantes para ayudar a desarrollar aplicaciones rápidamente. Estas herramientas también generan código que se agrega al proyecto.  
  
 Puede ver las infracciones de reglas que el análisis de código detecta en el código generado. Sin embargo, no puede verlos si no se puede ver y mantener el código que contiene la infracción.  
  
 El **Suprimir resultados del código generado** casilla de verificación en la página de propiedades de análisis de código de un proyecto le permite seleccionar si desea ver las advertencias de análisis de código del código generado por una herramienta de terceros.  
  
> [!NOTE]
>  Esta opción no suprime los errores de análisis de código y las advertencias de código generado cuando los errores y advertencias aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir las advertencias para el código generado en un proyecto  
  
1.  Haga clic en el proyecto en el Explorador de soluciones y, a continuación, haga clic en **propiedades**.  
  
2.  Haga clic en **de análisis de código**.  
  
3.  Seleccione el **Suprimir resultados del código generado** casilla de verificación.