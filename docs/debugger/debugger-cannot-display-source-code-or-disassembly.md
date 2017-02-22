---
title: "El depurador no puede mostrar el c&#243;digo fuente o el desensamblado | Microsoft Docs"
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
  - "código de desensamblado, errores"
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# El depurador no puede mostrar el c&#243;digo fuente o el desensamblado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error reza como sigue:  
  
 El depurador no puede mostrar el código fuente o el desensamblado disponibles para la ubicación actual donde se ha detenido la ejecución.  
  
 Este error puede producirse por una serie de motivos:  
  
-   Puede haber alcanzado un punto de interrupción en una ubicación para la que no existe código fuente, mientras depura un lenguaje que no admite desensamblado.  Abra la ventana **Puntos de interrupción**, localice el punto de interrupción y elimínelo.  
  
-   Si está depurando un script, puede haber alcanzado un punto de interrupción cuando no existía ningún subproceso en el programa.  Elija **Paso** o **Continuar** en el menú **Depurar** para reanudar la depuración.  
  
-   Las consideraciones de seguridad pueden haber impedido que el depurador leyera datos de la pila, subprocesos, registros u otra información de contexto del programa que se está depurando.  Esta situación es bastante probable si se está depurando una aplicación Web y no se dispone de permiso para obtener acceso al directorio virtual.  Haga que la seguridad para el directorio virtual sea "anónimo" y pruebe de nuevo.  
  
## Vea también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)