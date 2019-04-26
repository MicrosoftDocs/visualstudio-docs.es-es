---
title: Preferencias de estilo del código
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975364"
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. En el cuadro de diálogo **Opciones**, seleccione **Editor de texto** > [**C#** o **Básica**] > **Estilo de código** > **General**.

Cada elemento de la lista muestra una vista previa de la preferencia cuando se selecciona:

::: moniker range="vs-2017"

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opciones de estilo de código](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Las opciones que se establecen en esta ventana se aplican a la cuenta de personalización de Visual Studio y no están asociadas con un proyecto o código base determinado. Además, no se aplican en tiempo de compilación, lo que incluye las compilaciones de integración continua (CI). Si quiere asociar las preferencias de estilo de código con el proyecto y aplicar los estilos durante la compilación, especifique las preferencias en un [archivo .editorconfig](#editorconfig-files).

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Comportamiento del editor en Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>Archivos EditorConfig

La configuración del estilo del código para .NET también se puede especificar mediante la incorporación de un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) al proyecto.

::: moniker range=">=vs-2019"

Haga clic en **Generar archivo .editorconfig desde la configuración** para generar automáticamente un archivo .editorconfig de estilo de codificación basado en las opciones que estableció en esta página **Opciones**.

![Generación del archivo .editorconfig desde la configuración en VS 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

Los archivos EditorConfig están asociados con un código base en lugar de una cuenta de personalización de Visual Studio. La configuración de un archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. Use un archivo EditorConfig cuando quiera aplicar los estilos de codificación para todos los colaboradores en el repositorio o proyecto.

## <a name="preference-and-severity"></a>Preferencia y gravedad

Para cada configuración de estilo de código de esta página, puede establecer los valores de **Preferencia** y **Gravedad** con las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguno**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Ninguno**. El icono de bombilla ![Bombilla](media/light-bulb-dropdown.png), de bombilla de error ![Bombilla de error](media/error-bulb.png) o de destornillador ![Destornillador](media/screwdriver.png) de **Acciones rápidas** aparece cuando se usa un estilo no preferido, y puede elegir una opción en la lista **Acciones rápidas** para volver a escribir código de forma automática para el estilo preferido.

## <a name="format-document-command"></a>Comando Dar formato al documento

Puede configurar el comando **Dar formato al documento** (**Edición** > **Avanzado** > **Dar formato al documento**) para realizar una limpieza de código adicional en un archivo, como quitar y ordenar instrucciones Using o aplicar preferencias de estilo de código. Puede definir qué configuración quiere que **Dar formato al documento** aplique en la [página de opciones Formato](reference/options-text-editor-csharp-formatting.md#format-document-settings).

La limpieza de código respeta la configuración establecida en un archivo *.editorconfig* o, si falta dicha regla o archivo, la establecida en **Herramientas** > **Opciones** > **Editor de texto** > **C#** > [**Estilo de código** o **Formato**].

La primera vez que desencadena el comando **Dar formato al documento** en Visual Studio, una barra amarilla de información le pide que configure las opciones de limpieza de código.

> [!TIP]
> Las reglas configuradas con una gravedad de **Ninguna** no participan en la limpieza de código, pero se pueden aplicar de manera individual a través del menú **Acciones rápidas y refactorizaciones**.

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamiento del editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)