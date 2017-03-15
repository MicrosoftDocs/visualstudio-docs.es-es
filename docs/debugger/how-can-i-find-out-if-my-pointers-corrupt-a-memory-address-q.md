---
title: "C&#243;mo averiguar si los punteros da&#241;an una direcci&#243;n de memoria | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "direcciones, punteros que dañan direcciones de memoria"
  - "dirección de memoria dañada"
  - "depurar [C++], daño en la memoria"
  - "dirección de memoria dañada por punteros"
  - "memoria, daños"
  - "punteros, dañar direcciones de memoria"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo averiguar si los punteros da&#241;an una direcci&#243;n de memoria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descripción del problema  
 Parece que uno de los punteros está dañando la memoria en la dirección 0x00408000.  ¿Cómo se puede averiguar lo que está ocurriendo allí?  
  
## Soluciones  
  
#### Compruebe si el montón está dañado  
  
-   La mayoría de los daños en la memoria se deben en realidad a que el montón está dañado.  Pruebe a usar la utilidad de marcas global \(gflags.exe\) o pageheap.exe.  Vea [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### Para averiguar dónde se ha modificado la dirección de la memoria  
  
1.  Establezca un punto de interrupción de datos en 0x00408000.  Vea [Establecer un punto de interrupción de cambio de datos \(solo C\+\+ nativo\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  Cuando alcance el punto de interrupción, utilice la ventana **Memoria** para ver el contenido de la memoria a partir de la dirección 0x00408000.  Para obtener más información, vea [Memoria \(Ventana\)](../debugger/memory-windows.md).  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)