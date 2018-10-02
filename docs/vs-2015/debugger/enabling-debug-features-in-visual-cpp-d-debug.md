---
title: Habilitación de características de depuración en Visual C++ (-D_DEBUG) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67de755105f30ee4a88daeef26bc29bc9841ae39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575798"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Habilitar las características de depuración en Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [habilitar características de depuración de Visual C++ (-D_DEBUG)](https://docs.microsoft.com/visualstudio/debugger/enabling-debug-features-in-visual-cpp-d-debug).  
  
En [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], las características de depuración, como las aserciones se habilitan al compilar el programa con el símbolo **_DEBUG** definido. Puede definir **_DEBUG** en uno de dos maneras:  
  
-   Especificar **#define _DEBUG** en el código fuente, o  
  
-   Especifique el **/D_DEBUG** opción del compilador. (Si crea el proyecto en Visual Studio mediante los asistentes, **/D_DEBUG** se define automáticamente en la configuración de depuración.)  
  
 Cuando **_DEBUG** está definido, el compilador compila las secciones de código entre **#ifdef _DEBUG** y `#endif`.  
  
 La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC. Los archivos de encabezado MFC determinan la versión correcta de la biblioteca MFC debe vincular con basándose en los símbolos definidos, como **_DEBUG** y **_UNICODE**. Para obtener más información, consulte [versiones de la biblioteca MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



