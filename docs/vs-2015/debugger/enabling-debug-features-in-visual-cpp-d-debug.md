---
title: Habilitación de características de depuración en Visual C++ (-D_DEBUG) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cbaa01cfde69db639f354f3d68bd6bbee82efc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989376"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Habilitar las características de depuración en Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], las características de depuración, como las aserciones, se habilitan al compilar el programa con el símbolo **_DEBUG** definido. Puede definir **_DEBUG** de dos maneras:  
  
- Especifique **#define _DEBUG** en el código fuente o  
  
- Especifique la opción de compilador **/D_DEBUG**. Si crea el proyecto en Visual Studio utilizando asistentes, **/D_DEBUG** se define automáticamente en la configuración de depuración.  
  
  Cuando se define **_DEBUG**, el compilador compila las secciones de código entre **#ifdef _DEBUG** y `#endif`.  
  
  La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC. Los archivos de encabezado de MFC determinan la versión correcta de la biblioteca MFC con la que se debe vincular a partir de los símbolos que haya definido, como **_DEBUG** y **_UNICODE**. Para obtener información detallada, vea [Versiones de la biblioteca MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
