---
title: "C&#243;mo: Cambiar a otro subproceso durante la depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "subprocesos, cambiar [depuración]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Cambiar a otro subproceso durante la depuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al depurar una aplicación multithreading, puede utilizar uno de los métodos existentes para intercambiar entre el contexto del subproceso en el que ha estado trabajando y otro subproceso.  
  
### Para pasar a otro subproceso que aparezca en la ventana Subprocesos  
  
-   Haga doble clic en el subproceso.  
  
### Para cambiar a un subproceso en una ventana de código fuente  
  
-   En el margen interior izquierdo, haga clic con el botón secundario en un indicador del subproceso, apunte a **Cambiar a** y, a continuación, haga clic en el nombre del subproceso al que desea cambiar.  El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.  
  
     Si no aparece ningún indicador, haga clic con el botón secundario del mouse en la ventana **Subprocesos** y compruebe que **Mostrar subprocesos en código fuente** está seleccionado.  
  
### Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración  
  
1.  En la barra de herramientas **Ubicación de depuración**, haga clic en el cuadro **Subproceso**.  
  
2.  En la lista, haga clic en el subproceso al que desee cambiar.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)