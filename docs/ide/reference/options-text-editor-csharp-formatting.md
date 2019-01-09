---
title: Opciones de formato del editor de C#
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b3c4aa17e31797c9c8bbfa1a931369f371977e26
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946414"
---
# <a name="options-text-editor-c-code-style-formatting"></a>Opciones, editor de texto, C#, estilo de código, formato

Use la página de opciones **Formato** para establecer las opciones de formato de código en el editor de código. Para acceder a esta página de opciones, elija **Herramientas** > **Opciones**. En el cuadro de diálogo **Opciones**, elija **Editor de texto** > **C#** > **Estilo de código** > **Formato**.

## <a name="general-page"></a>Página general

### <a name="general-settings"></a>Configuración general

Esta configuración afecta al *momento* en que el editor de código aplica las opciones de formato al código.

|Etiqueta|Descripción|
|-----------|-----------------|
|**Dar formato automáticamente al escribir**|Si está desactivada, las opciones **Dar formato automáticamente a la instrucción al introducir ;** y **Dar formato automáticamente al bloque al introducir }** están desactivadas.|
|**Dar formato automáticamente a la instrucción al introducir ;**|Si está activada, da formato a las instrucciones a su finalización según las opciones de formato seleccionadas para el editor.|
|**Dar formato automáticamente al bloque al introducir }**|Si está activada, da formato a los bloques de código según las opciones de formato seleccionadas para el editor de código tan pronto como complete el bloque de código.|
|**Dar formato automáticamente al volver**|Si está activada, da formato al texto cuando se presiona **Entrar** para ajustarlo a las opciones de formato seleccionadas para el editor.|
|**Dar formato automáticamente al pegar**|Si está activada, da formato al texto pegado en el editor para ajustarlo a las opciones de formato seleccionadas para el editor.|

### <a name="format-document-settings"></a>Configuración para dar formato al documento

Estos valores configuran el comando **Dar formato al documento** para realizar la limpieza de código adicional en un archivo. Para más información sobre cómo se aplican estas opciones, vea [Dar formato al documento](../code-styles-and-quick-actions.md#format-document-command).

|Etiqueta|Descripción|EditorConfig correspondiente y Herramientas > Reglas de opciones|
|-----------|-----------------|-----------------|-----------------|
|**Aplicar todas las reglas de formato de C# (sangría, ajuste, espaciado)**|El comando **Dar formato al documento** siempre corrige problemas de formato. No se puede cambiar esta opción.| [Opciones de EditorConfig Core](../../ide/create-portable-custom-editor-options.md)<br/>[Opciones de formato de .NET EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Formato** > [**Sangría** o **Nuevas líneas** o **Espaciado** o **Ajuste de texto**]|
|**Realizar limpieza de código adicional durante la aplicación de formato**|Cuando se selecciona, se aplican revisiones para las reglas especificadas a continuación en el comando **Edit.FormatDocument**.| N/D |
|**Quitar directivas Using innecesarias**|Cuando se selecciona, se quitan las directivas `using` innecesarias cuando se desencadena **Edit.FormatDocument**.| N/D |
|**Ordenar instrucciones Using**|Cuando se selecciona, se ordenan las directivas `using` cuando se desencadena **Edit.FormatDocument**.| dotnet_sort_system_directives_first<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Avanzado** > **Aplicar primero directivas "System" al ordenar instrucciones Using** |
|**Agregar o quitar llaves en instrucciones de control de una sola línea**|Cuando se selecciona, se agregan o se quitan las llaves de instrucciones de control de línea única cuando se desencadena **Edit.FormatDocument**.| csharp_prefer_braces<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias del bloque de código** > **Preferir llaves** |
|**Agregar modificadores de accesibilidad**|Cuando se selecciona, se agregan los modificadores de accesibilidad que faltan cuando se desencadena **Edit.FormatDocument**.| dotnet_style_require_accessibility_modifiers |
|**Ordenar modificadores de accesibilidad**|Cuando se selecciona, se ordenan los modificadores de accesibilidad cuando se desencadena **Edit.FormatDocument**.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Aplicar preferencias de cuerpo de expresiones o bloques**|Cuando se selecciona, se convierten los miembros con forma de expresión para bloquear cuerpos, o viceversa, cuando se desencadena **Edit.FormatDocument**.| [Opciones de miembros con forma de expresión de EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de expresión** > **Usar cuerpo de expresiones para los métodos, constructores, etcétera.** |
|**Aplicar preferencias de tipos implícitos o explícitos**|Cuando se selecciona, se convierte `var` al tipo explícito, o viceversa, cuando se desencadena **Edit.FormatDocument**.| [Opciones de EditorConfig de tipo explícito](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de 'var'** |
|**Aplicar preferencias de variables "out" insertadas**|Cuando se selecciona, se usan variables `out` insertadas siempre que sea posible cuando se desencadena **Edit.FormatDocument**.| csharp_style_inlined_variable_declaration<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de variable** > **Preferir declaración de variable insertada** |
|**Aplicar preferencias de tipo de marco o lenguaje**|Cuando se selecciona, convierte los tipos de lenguaje en tipos de marco, o viceversa, cuando se desencadena **Edit.FormatDocument**.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de tipo predefinido** |
|**Aplicar preferencias de inicialización de objeto o colección**|Cuando se selecciona, se usan inicializadores de objeto y colección siempre que sea posible cuando se desencadena **Edit.FormatDocument**.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de expresión** > **Preferir inicializador de objeto** o **Preferir inicializador de colección** |
|**Aplicar preferencias de calificación "this."**|Cuando se selecciona, se aplican las preferencias de `this.` cuando se desencadena **Edit.FormatDocument**.| [Opciones de EditorConfig de calificación de this.](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de this.** |
|**Cuando sea posible, hacer que los campos privados sean de solo lectura**|Cuando se selecciona, convierte los campos privados `readonly` siempre que sea posible cuando se desencadena **Edit.FormatDocument**.| dotnet_style_readonly_field<br/><br/>**Herramientas** > **Opciones** > **Editor de texto** > **C#** > **Estilo de código** > **Preferencias de campo** > **Preferir readonly** |
|**Quitar conversiones innecesarias**|Cuando se selecciona, se quitan las conversiones innecesarias siempre que sea posible cuando se desencadena **Edit.FormatDocument**.| N/D |
|**Quitar variables no usadas**|Cuando se selecciona, se quitan las variables no usadas cuando se desencadena **Edit.FormatDocument**.| N/D |

![Configuración de limpieza de código para C# en Visual Studio](media/format-document-settings.png)

## <a name="preview-windows"></a>Ventanas de vista previa

Las subpáginas **Sangría**, **Nuevas líneas**, **Espaciado** y **Ajuste** muestran cada uno una ventana de vista previa en la parte inferior. La ventana de vista previa muestra el efecto de cada opción. Para usar la ventana de vista previa, seleccione una opción de formato. La ventana de vista previa muestra un ejemplo de la opción seleccionada. Cuando cambia la configuración (activando o desactivando una casilla o un botón de radio), la ventana de vista previa se actualiza para mostrar el efecto de la nueva configuración.

## <a name="indentation-remarks"></a>Comentarios de sangría

Las opciones de sangría en las páginas **Pestañas** de cada idioma solo determinan dónde coloca el cursor el Editor de código cuando se presiona **Entrar** al final de una línea. Las opciones de sangría en **Formato** se aplican cuando se da formato al código automáticamente, por ejemplo, cuando pega código en el archivo con la opción **Ajustar sangría al pegar** seleccionada, y cuando el bloque al que se está dando formato se escribe manualmente.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)