---
title: 'Cómo: utilizar comprobaciones nativas en tiempo de ejecución | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4efbb4e151ea47f655f0b28e19d2811d5541e944
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798760"
---
# <a name="how-to-use-native-run-time-checks"></a>Cómo: Utilizar comprobaciones nativas en tiempo de ejecución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual C++, puede realizar [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) nativas para detectar errores en tiempo de ejecución, tales como:  
  
- Daños en el puntero de la pila  
  
- Saturación de matrices locales  
  
- Daños en la pila  
  
- Dependencias en variables locales sin inicializar  
  
- Pérdida de datos en una asignación a una variable corta.  
  
  Si utiliza **/RTC** con una generación optimizada (**/O**), obtendrá un error del compilador. Si utiliza un pragma `runtime_checks` en una versión optimizada, el pragma no surte ningún efecto.  
  
  Cuando se depura un programa con las comprobaciones en tiempo de ejecución habilitadas, la acción predeterminada es la de que el programa se detenga y se interrumpa su depuración cuando se produzca un error en tiempo de ejecución. Puede cambiar este comportamiento predeterminado para cualquier comprobación en tiempo de ejecución. Para obtener más información, consulte [administrar excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
  Los siguientes procedimientos describen cómo habilitar las comprobaciones en tiempo de ejecución nativas en una versión de depuración y cómo modificar el comportamiento de la comprobación en tiempo de ejecución nativa.  
  
  Los demás temas de esta sección contienen información sobre:  
  
- [Personalizar las comprobaciones en tiempo de ejecución con la biblioteca en tiempo de ejecución de C](../debugger/native-run-time-checks-customization.md)  
  
- [Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Para habilitar las comprobaciones nativas en tiempo de ejecución en una versión de depuración  
  
-   Utilice la opción **/RTC** y vincule la versión de depuración de una biblioteca C en tiempo de ejecución (/MDd, por ejemplo).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Para modificar el comportamiento de las comprobaciones nativas en tiempo de ejecución  
  
-   Utilice la directiva pragma `runtime_checks` .  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Comprobar errores en tiempo de ejecución](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





