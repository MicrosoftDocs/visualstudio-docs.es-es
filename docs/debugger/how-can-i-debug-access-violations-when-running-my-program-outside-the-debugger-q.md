---
title: "C&#243;mo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depuración de infracción de acceso"
  - "depurar [Visual Studio], infracciones de acceso"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descripción del problema  
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso.  ¿Cómo se puede depurar este problema?  
  
## Soluciones  
 Establezca la opción [Depuración Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md) y ejecute el programa de forma independiente hasta que se produzca la infracción de acceso.  A continuación, en el cuadro de diálogo **Infracción de acceso**, se puede hacer clic en **Cancelar** para iniciar el depurador.  
  
 Vea también el artículo Q133174 de Knowledge Base, "How to Locate Where a General Protection \(GP\) Fault Occurs". Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o realizando búsquedas en [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)