---
title: "No hay c&#243;digo fuente disponible | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "No hay código fuente disponible para la ubicación actual (cuadro de diálogo)"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# No hay c&#243;digo fuente disponible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proyecto no contiene código fuente para el código que se está intentando ver.  El motivo habitual es hacer doble clic en un módulo que no tiene código fuente en la **Ventana Pila de llamadas** o en la **Ventana Subprocesos**.  Puede seguir depurando, pero no puede utilizar la ventana de código fuente para establecer puntos de interrupción y realizar otras acciones en dicha ubicación.  Si necesita establecer un punto de interrupción, utilice la **Ventana Desensamblado** en su lugar.  
  
 En las Páginas de propiedades de la solución, puede cambiar los directorios en los que el depurador busca archivos de código fuente e indicar al depurador que omita los archivos de código fuente seleccionados.  Vea [Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución \(Cuadro de diálogo\)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Buscar código fuente**  
 Haga clic en este vínculo para abrir un cuadro de diálogo en el que puede buscar código fuente.  
  
 **Mostrar desensamblado**  
 Inicia la **Ventana Desensamblado**.  
  
 **Mostrar siempre el desensamblado de los archivos de código fuente que falten**  
 Seleccione esta opción para que aparezca automáticamente la **Ventana Desensamblado** cuando no haya disponible ningún código fuente.  Esta configuración también se puede cambiar en el cuadro de diálogo **Opciones**, categoría **Depuración**, página **General**. Para ello active o desactive **Mostrar desensamblado si el código fuente no está disponible**.  
  
## Vea también  
 [Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución \(Cuadro de diálogo\)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)