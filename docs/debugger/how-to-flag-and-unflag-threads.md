---
title: "C&#243;mo: Marcar y quitar marcadores de subprocesos | Microsoft Docs"
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
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Marcar y quitar marcadores de subprocesos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede marcar un subproceso al que desee prestar atención especial con un icono en las ventanas **Subprocesos**, **Pilas paralelas**, **Inspección paralela** y **Subprocesos de GPU**.  Este icono ayuda a distinguir estos subprocesos marcados de otros.  
  
 Los subprocesos marcados también reciben un tratamiento especial en la lista **Subproceso** de la barra de herramientas **Ubicación de depuración**.  Esta lista puede mostrar todos los subprocesos o solo los marcados.  Cuando marca un subproceso, la lista **Subproceso** cambia automáticamente y muestra los subprocesos marcados solo, pero puede volverla a cambiar para mostrar todos los subprocesos.  
  
### Para marcar o desmarcar un subproceso utilizando la ventana Subprocesos  
  
-   En la ventana **Subprocesos**, busque el subproceso que le interesa y haga clic en el icono de marca para seleccionar o borrar la marca.  
  
### Para quitar los marcadores de todos los subprocesos  
  
-   En la ventana **Subprocesos**, haga clic con el botón secundario del mouse en cualquier subproceso y después haga clic en **Quitar marca de todos los subprocesos**.  
  
### Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana de depuración.  
  
### Para marcar Solo mi código  
  
1.  En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.  
  
2.  En la lista desplegable **Marcar solo mi código**.  
  
### Para marcar subprocesos que están asociados a módulos seleccionados  
  
1.  En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.  
  
2.  En la lista desplegable, haga clic en **Marcar selección de módulos personalizados**.  
  
3.  En el cuadro de diálogo **Seleccionar módulos**, seleccione los módulos que desea.  
  
4.  \(Opcional\) En el cuadro **Buscar**, escriba una cadena para buscar módulos concretos.  
  
5.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)