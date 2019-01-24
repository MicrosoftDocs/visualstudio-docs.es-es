---
title: Sugerencias para depurar subprocesos en código nativo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1852e2d0b3e773e5be0f3f60ad191056a4af0889
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775009"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Sugerencias para depurar subprocesos en código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación se muestran algunas sugerencias que puede usar al depurar subprocesos en código nativo:  
  
-   Puede ver el contenido del bloque de información de subprocesos escribiendo `@TIB` en el **inspección** ventana o **Inspección rápida** cuadro de diálogo.  
  
-   Puede ver el último código de error para el subproceso actual escribiendo `@Err` en el **inspección** ventana o **Inspección rápida** cuadro de diálogo.  
  
-   Las funciones de las bibliotecas en tiempo de ejecución de C (CRT) pueden ser útiles para depurar una aplicación multiproceso. Para obtener más información, consulte [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



