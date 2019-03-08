---
title: Preferencias de estilo del código
ms.date: 03/10/2017
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 1f5ad2f5860c148d4bb9d0ee026eee9b1e83c74c
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223135"
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. En el cuadro de diálogo **Opciones**, seleccione **Editor de texto** > [**C#** o **Básica**] > **Estilo de código** > **General**. Las opciones configuradas en esta ventana se aplican solamente a la máquina local.

Cada elemento de la lista muestra una vista previa de la preferencia cuando se selecciona:

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Comportamiento del editor en Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferencia y gravedad

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** usando las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguno**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Ninguno**. El icono de bombilla ![Bombilla](media/vs2015_lightbulbsmall.png), de bombilla de error ![Bombilla de error](media/error-bulb.png) o de destornillador ![Destornillador](media/screwdriver.png) de **Acciones rápidas** aparece cuando se usa un estilo no preferido, y puede elegir una opción en la lista **Acciones rápidas** para volver a escribir código de forma automática para el estilo preferido.

## <a name="editorconfig-files"></a>Archivos EditorConfig

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). La configuración del archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. El archivo EditorConfig sirve para aplicar y configurar el estilo de codificación de todo el repositorio o proyecto.

## <a name="format-document-command"></a>Comando Dar formato al documento

Puede configurar el comando **Dar formato al documento** (**Edición** > **Avanzado** > **Dar formato al documento**) para realizar una limpieza de código adicional en un archivo, como quitar y ordenar instrucciones Using o aplicar preferencias de estilo de código. Puede definir qué configuración quiere que **Dar formato al documento** aplique en la [página de opciones Formato](reference/options-text-editor-csharp-formatting.md#format-document-settings).

La limpieza de código respeta la configuración establecida en un archivo *.editorconfig* o, si falta dicha regla o archivo, la establecida en **Herramientas** > **Opciones** > **Editor de texto** > **C#** > [**Estilo de código** o **Formato**].

La primera vez que desencadena el comando **Dar formato al documento** en Visual Studio, una barra amarilla de información le pide que configure las opciones de limpieza de código.

> [!TIP]
> Las reglas configuradas como **ninguna** en un archivo *.editorconfig* no participan en la limpieza de código, pero se pueden aplicar individualmente a través del menú **Acciones rápidas y refactorizaciones**.

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamiento del editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)