---
title: Sugerencias para depurar subprocesos en código nativo | Documentos de Microsoft
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c98f6bb1a738111d32b26c5b923abe41367e621e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Sugerencias para depurar subprocesos en código nativo
A continuación se muestran algunas sugerencias que puede usar al depurar subprocesos en código nativo:  
  
-   Puede ver el contenido del bloque de información de subprocesos escribiendo `@TIB` en el **inspección** ventana o **Inspección rápida** cuadro de diálogo.  
  
-   Puede ver el último código de error del subproceso actual escribiendo `@Err` en el **inspección** ventana o **Inspección rápida** cuadro de diálogo.  
  
-   Las funciones de las bibliotecas en tiempo de ejecución de C (CRT) pueden ser útiles para depurar una aplicación multiproceso. Para obtener más información, consulte [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)