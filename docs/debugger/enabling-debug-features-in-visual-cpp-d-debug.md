---
title: "Habilitar características de depuración en Visual C++ (-D_DEBUG) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f1067ee5b60b8a8a402c9612357f2d83b6da138
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Habilitar las características de depuración en Visual C++ (/D_DEBUG)
En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], características de depuración, como las aserciones, se habilitan al compilar el programa con el símbolo **_DEBUG** definido. Puede definir **_DEBUG** en uno de dos maneras:  
  
-   Especifique **#define _DEBUG** en el código fuente, o  
  
-   Especifique el **/D_DEBUG** opción del compilador. (Si crea el proyecto en Visual Studio utilizando asistentes, **/D_DEBUG** se define automáticamente en la configuración de depuración.)  
  
 Cuando **_DEBUG** está definido, el compilador compila las secciones de código entre **#ifdef _DEBUG** y `#endif`.  
  
 La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC. Los archivos de encabezado MFC determinan la versión correcta de la biblioteca MFC debe vincular con en función de los símbolos definidos, como **_DEBUG** y **_UNICODE**. Para obtener más información, consulte [versiones de la biblioteca MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)