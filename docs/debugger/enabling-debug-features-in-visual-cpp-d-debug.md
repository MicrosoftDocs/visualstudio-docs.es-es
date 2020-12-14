---
title: Habilitación de las características de depuración en proyectos de C++ (-D_DEBUG) | Microsoft Docs
description: En Visual C++, puede habilitar características de depuración si define _DEBUG. Obtenga información sobre cómo hacerlo y cómo vincular un programa de MFC para depurarlo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1a2ead92108d66b54342019fc19702e7a6e53575
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862938"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Habilitación de las características de depuración en proyectos de C++ (-D_DEBUG)
En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], las características de depuración, como las aserciones, se habilitan al compilar el programa con el símbolo **_DEBUG** definido. Puede definir **_DEBUG** de dos maneras:

- Especifique **#define _DEBUG** en el código fuente o

- Especifique la opción de compilador **/D_DEBUG**. Si crea el proyecto en Visual Studio utilizando asistentes, **/D_DEBUG** se define automáticamente en la configuración de depuración.

  Cuando se define **_DEBUG**, el compilador compila las secciones de código entre **#ifdef _DEBUG** y `#endif`.

  La configuración de depuración de un programa MFC debe vincular con la versión de depuración de la biblioteca MFC. Los archivos de encabezado de MFC determinan la versión correcta de la biblioteca MFC con la que se debe vincular a partir de los símbolos que haya definido, como **_DEBUG** y **_UNICODE**. Para obtener información detallada, vea [Versiones de la biblioteca MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Vea también
- [Depuración de código nativo](../debugger/debugging-native-code.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)