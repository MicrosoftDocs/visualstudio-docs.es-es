---
title: Administrar herramientas externas
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1caf72ea2dccd9dfe2978726834e8066a9f5b56b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652385"
---
# <a name="manage-external-tools"></a>Administrar herramientas externas

Se puede llamar a herramientas externas desde Visual Studio mediante el menú **Herramientas**. Algunas herramientas predeterminadas están disponibles en el menú **Herramientas**, pero se puede personalizar el menú al agregar otros archivos ejecutables propios.

## <a name="tools-available-on-the-tools-menu"></a>Herramientas disponibles en el menú Herramientas

El menú **Herramientas** contiene varios comandos integrados, como:

::: moniker range="vs-2017"

* **Extensiones y actualizaciones** para [administrar Extensiones de Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Administrador de fragmentos de código** para [organizar fragmentos de código](code-snippets.md)
* **Personalizar** para [personalizar menús y barras de herramientas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opciones** para [establecer varias opciones diferentes para el IDE de Visual Studio y otras herramientas](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Administrador de fragmentos de código** para [organizar fragmentos de código](code-snippets.md)
* **Personalizar** para [personalizar menús y barras de herramientas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opciones** para [establecer varias opciones diferentes para el IDE de Visual Studio y otras herramientas](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Agregar nuevas herramientas al menú Herramientas

Puede agregar una herramienta externa para que aparezca en el menú **Herramientas**.

1. Para abrir el cuadro de diálogo **Herramientas externas**, elija **Herramientas** > **Herramientas externas**.

1. Haga clic en **Agregar** y, después, rellene la información. Por ejemplo, la entrada siguiente hace que el **Explorador de Windows** se abra en el directorio del archivo que tiene abierto en Visual Studio:

   * Título: `Open File Location`

   * Comando: `explorer.exe`

   * Argumentos: `/root, "$(ItemDir)"`

   ![Cuadro de diálogo Herramientas externas](media/external-tools-dialog.png)

Lo siguiente es una lista completa de los argumentos que se pueden utilizar al definir una herramienta externa:

|Name|Argumento|DESCRIPCIÓN|
|----------|--------------|-----------------|
|Ruta de acceso del elemento|$(ItemPath)|Nombre de archivo completo del archivo actual (unidad + ruta de acceso + nombre de archivo).|
|Directorio del elemento|$(ItemDir)|Directorio del archivo actual (unidad + ruta de acceso).|
|Nombre de archivo del elemento|$(ItemFilename)|Nombre de archivo del archivo actual (nombre de archivo).|
|Extensión del elemento|$(ItemExt)|Extensión del nombre de archivo del archivo actual.|
|Línea actual|$(CurLine)|Posición de línea actual del cursor en la ventana de código.|
|Columna actual|$(CurCol)|Posición de columna actual del cursor en la ventana de código.|
|Texto actual|$(CurText)|Texto seleccionado.|
|Ruta de acceso de destino|$(TargetPath)|Nombre de archivo completo del elemento que se va a compilar (unidad + ruta de acceso + nombre de archivo).|
|Directorio de destino|$(TargetDir)|Directorio del elemento que se va a compilar.|
|Nombre de destino|$(TargetName)|Nombre de archivo del elemento que se va a compilar.|
|Extensión de destino|$(TargetExt)|Extensión del nombre de archivo del elemento que se va a compilar.|
|Directorio binario|$(BinDir)|Ubicación final del archivo binario que se va a compilar (definida como unidad + ruta de acceso).|
|Directorio del proyecto|$(ProjectDir)|Directorio del proyecto actual (unidad + ruta de acceso).|
|Nombre de archivo del proyecto|$(ProjectFileName)|Nombre de archivo del proyecto actual (unidad + ruta de acceso + nombre de archivo).|
|Directorio de la solución|$(SolutionDir)|Directorio de la solución actual (unidad + ruta de acceso).|
|Nombre de archivo de la solución|$(SolutionFileName)|Nombre de archivo de la solución actual (unidad + ruta de acceso + nombre de archivo).|

> [!NOTE]
> La barra de estado del IDE muestra las variables **Línea actual** y **Columna actual** para indicar dónde se encuentra el punto de inserción en el **Editor de código** activo. La variable **Texto actual** devuelve el texto o el código seleccionado en esa ubicación.

## <a name="see-also"></a>Vea también

- [Herramientas de compilación de C/C++](/cpp/build/reference/c-cpp-build-tools)
