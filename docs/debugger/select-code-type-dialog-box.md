---
title: Seleccionar tipo de código (Cuadro de diálogo) | Microsoft Docs
description: Obtenga información sobre el cuadro de diálogo de Visual Studio Seleccionar tipo de código. Para abrir este cuadro de diálogo, abra el cuadro de diálogo Asociar al proceso y haga clic en el botón Seleccionar.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7fb7b7625e8e08e291f4f27606d03f9066828e0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903489"
---
# <a name="select-code-type-dialog-box"></a>Seleccionar tipo de código (Cuadro de diálogo)

Para abrir este cuadro de diálogo, abra el cuadro de diálogo **Asociar al proceso** y haga clic en el botón **Seleccionar**.

**Determinar automáticamente el tipo de código para depurar** Se seleccionará el depurador adecuado en función del tipo de código que se está ejecutando.

**Depurar estos tipos de código:** En la lista proporcionada, elija el tipo de código que desee depurar. Esto puede ser útil cuando se [soluciona un error al asociar](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Esta opción restringe la detección solo a los tipos de código que desea depurar.

::: moniker range=">=vs-2019"
- Blazor WebAssembly: Blazor WebAssembly del lado cliente
- GPU (emulador de software): código de C++ que se ejecuta en un emulador de software de GPU
- JavaScript (Chrome): JavaScript que se ejecuta en Chrome
- JavaScript (Microsoft Edge - Chromium): JavaScript que se ejecuta en Microsoft Edge basado en Chromium para Windows 10
- Depurador de CDP para JavaScript (V3): versión 3 del protocolo Chrome DevTools, que se usa para la depuración en un cliente de CDP
- Administrado (CoreCLR): .NET Core
- Administrado (compilación nativa): código de C++/CLR
- Administrado (v3.5, v3.0 y v2.0): código de .NET Framework para .NET Framework 2.0 y versiones posteriores (hasta la versión 3.5)
- Administrado (v.4.6, v4.5 y v4.0): código de .NET Framework para .NET Framework 4.0 y versiones posteriores
- Nativo: C y C++
- Depuración de Node.js: código hospedado por el entorno de ejecución de Node.js
- Python: Python 
- Script: especifica el depurador de script general para JavaScript. Use opciones más restrictivas si se aplican a su escenario, como JavaScript (Chrome).
- T-SQL: Transact-SQL
- Unity: Unity
- Modo de compatibilidad administrado: especifica el depurador heredado para el código administrado, para su uso habitual en la depuración en modo mixto con código de C++ y CLR (habilita la opción Editar y continuar para el modo mixto) o para admitir extensiones que tienen como destino el depurador heredado. En la mayoría de los escenarios de depuración en modo mixto, seleccione **Nativo** y los tipos de código **Administrado** adecuados en lugar de Modo de compatibilidad administrado.
::: moniker-end

Para la mayoría de los escenarios, no se admite la asociación de varios depuradores en la misma sesión de depuración. Puede hacerlo mediante una segunda instancia de Visual Studio.

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
