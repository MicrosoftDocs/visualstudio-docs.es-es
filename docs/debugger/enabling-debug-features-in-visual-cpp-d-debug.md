---
title: Habilitar las características de C++ depuración en proyectos (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 19d341cba47e0a3d2259cc57d239c63420095347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737957"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Habilitar las características de C++ depuración en los proyectos (/D_DEBUG)
En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], las características de depuración, como las aserciones, se habilitan al compilar el programa con el símbolo **_DEBUG** definido. Puede definir **_DEBUG** de dos maneras:

- Especifique **#define _DEBUG** en el código fuente o

- Especifique la opción de compilador **/D_DEBUG**. Si crea el proyecto en Visual Studio utilizando asistentes, **/D_DEBUG** se define automáticamente en la configuración de depuración.

  Cuando se define **_DEBUG**, el compilador compila las secciones de código entre **#ifdef _DEBUG** y `#endif`.

  La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC. Los archivos de encabezado de MFC determinan la versión correcta de la biblioteca MFC con la que se debe vincular a partir de los símbolos que haya definido, como **_DEBUG** y **_UNICODE**. Para obtener información detallada, vea [Versiones de la biblioteca MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Vea también
- [Depuración de código nativo](../debugger/debugging-native-code.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)