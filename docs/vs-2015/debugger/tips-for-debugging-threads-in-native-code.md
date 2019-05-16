---
title: Sugerencias para depurar subprocesos en código nativo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684868"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Sugerencias para depurar subprocesos en código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación se muestran algunas sugerencias que puede usar al depurar subprocesos en código nativo:  
  
- Puede ver el contenido del Bloque de información de subprocesos escribiendo `@TIB` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.  
  
- Puede ver el último código de error del subproceso actual escribiendo `@Err` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.  
  
- Las funciones de las bibliotecas en tiempo de ejecución de C (CRT) pueden ser útiles para depurar una aplicación multiproceso. Para obtener más información, consulte [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)
