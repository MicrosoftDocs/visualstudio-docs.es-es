---
title: Cómo averiguar si los punteros dañan una dirección de memoria | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8965ec268e5d236b9a33e5c3e8acfa35e51dcdb3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479317"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Cómo averiguar si los punteros dañan una dirección de memoria
## <a name="problem-description"></a>Descripción del problema  
 Parece que uno de los punteros está dañando la memoria en la dirección 0x00408000. ¿Cómo se puede averiguar lo que está ocurriendo allí?  
  
## <a name="solution"></a>Soluciones  
  
#### <a name="check-for-heap-corruption"></a>Compruebe si el montón está dañado  
  
-   La mayoría de los daños en la memoria se deben en realidad a que el montón está dañado. Pruebe a usar la utilidad de marcas global (gflags.exe) o pageheap.exe. Vea [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Para averiguar dónde se ha modificado la dirección de la memoria  
  
1.  Establezca un punto de interrupción de datos en 0x00408000. Vea [establecer un punto de interrupción de cambio de datos (solo C++ nativo)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Cuando se alcanza el punto de interrupción, utilice la **memoria** contenido de la ventana para ver la memoria a partir de 0 x 00408000. Para obtener más información, consulte [memoria (ventana)](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)