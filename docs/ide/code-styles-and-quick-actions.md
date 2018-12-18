---
title: Preferencias de estilo del código
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 718110b3339628052d8a4a2e3ebbcdd163707a97
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065266"
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. En el cuadro de diálogo **Opciones**, seleccione **Editor de texto** > [**C#** o **Básica**] > **Estilo de código** > **General**. Las opciones configuradas en esta ventana se aplican solamente a la máquina local.

Cada elemento de la lista muestra una vista previa de la preferencia cuando se selecciona:

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Comportamiento del editor en Visual Studio para Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferencia y gravedad

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** usando las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguno**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Ninguno**. El icono de bombilla de **Acciones rápidas** ![icono de bombilla pequeña](media/vs2015_lightbulbsmall.png) aparece cuando se usa un estilo no preferido y puede elegir una opción en la lista **Acciones rápidas** para volver a escribir código automáticamente para el estilo preferido.

## <a name="editorconfig-files"></a>Archivos EditorConfig

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). La configuración del archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. El archivo EditorConfig sirve para aplicar y configurar el estilo de codificación de todo el repositorio o proyecto.

## <a name="format-document-command"></a>Comando Dar formato al documento

En Visual Studio 2017 versión 15.8 y posteriores, puede configurar el comando **Dar formato al documento** (**Edición** > **Avanzado** > **Dar formato al documento**) para realizar la limpieza de código adicional en un archivo, como quitar y ordenar instrucciones using o aplicar las preferencias de estilo de código. Puede definir qué configuración quiere que **Dar formato al documento** aplique en la [página de opciones Formato](reference/options-text-editor-csharp-formatting.md#format-document-settings).

La limpieza de código respeta la configuración establecida en un archivo *.editorconfig* o, si falta dicha regla o archivo, la establecida en **Herramientas** > **Opciones** > **Editor de texto** > **C#** > [**Estilo de código** o **Formato**].

La primera vez que desencadena el comando **Dar formato al documento** en Visual Studio 2017, una barra amarilla de información le pedirá que configure las opciones de limpieza de código.

> [!TIP]
> Las reglas configuradas como **ninguna** en un archivo *.editorconfig* no participan en la limpieza de código, pero se pueden aplicar individualmente a través del menú **Acciones rápidas y refactorizaciones**.

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamiento del editor (Visual Studio para Mac)](/visualstudio/mac/editor-behavior)