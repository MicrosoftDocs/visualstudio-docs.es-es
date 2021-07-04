---
title: Visualización de archivos DLL y ejecutables
description: Consulte los archivos DLL y los ejecutables (.exe) que usa la aplicación en la ventana Módulos durante una sesión de depuración en Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385414"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Visualización de archivos DLL y ejecutables en la venta Módulos (C#, C++, Visual Basic, F#)

Durante la depuración en Visual Studio, en la ventana **Módulos** se muestra información sobre los archivos DLL y ejecutables ( *.exe*) que usa la aplicación.

> [!NOTE]
> La ventana Módulos no está disponible para la depuración de SQL o de script.

## <a name="use-the-modules-window"></a>Uso de la ventana Módulos

Para abrir la ventana Módulos mientras realiza la depuración, seleccione **Depurar** > **Ventanas** > **Módulos** (o bien, presione **Ctrl + Alt + U**).

De forma predeterminada, la ventana **Módulos** ordena los módulos por orden de carga. Para ordenar por cualquier columna de la ventana, seleccione el encabezado en la parte superior de la columna.

## <a name="load-symbols"></a>Cargar símbolos

En la columna **Estado de símbolos** de la ventana **Módulos** se muestra qué módulos han cargado símbolos de depuración. Si el estado es **Carga de símbolos omitida**, **No se puede encontrar o abrir el archivo PDB** o **Carga deshabilitada por la configuración de inclusión o exclusión**, puede cargar los símbolos manualmente. Para obtener más información sobre la carga y el uso de símbolos, vea [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Para cargar símbolos manualmente:**

1. En la ventana **Módulos**, haga clic con el botón derecho en un módulo para el que no se han cargado los símbolos.

   - Seleccione **Información de carga de símbolos** para obtener más información sobre por qué no se han cargado los símbolos.

   - Seleccione **Cargar símbolos** para cargar los símbolos de forma manual.

1. Si los símbolos no se cargan, seleccione **Configuración de símbolos** para abrir el cuadro de diálogo **Opciones** y especifique o cambie las ubicaciones de carga de símbolos.

   Puede descargar símbolos desde los servidores de símbolos públicos de Microsoft u otros servidores, o bien desde una carpeta del equipo. Para obtener más información, vea [Especificación de ubicaciones de símbolos y comportamiento de la carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Para cambiar la configuración del comportamiento de carga de símbolos:**

1. En la ventana **Módulos**, haga clic con el botón derecho en cualquier módulo.

1. Seleccione **Configuración de símbolos**.

1. Seleccione **Cargar todos los símbolos**, o bien los módulos que quiere incluir o excluir.

1. Seleccione **Aceptar**. Los cambios surten efecto en la siguiente sesión de depuración.

**Para cambiar el comportamiento de carga de símbolos de un módulo específico:**

1. En la ventana **Módulos**, haga clic con el botón derecho en el módulo.

1. En el menú contextual, seleccione o anule la selección de **Cargar siempre automáticamente**. Los cambios surten efecto en la siguiente sesión de depuración.

## <a name="see-also"></a>Vea también
- [Interrupción de la ejecución](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)