---
title: Opciones, editor de texto, general
description: Obtenga información sobre cómo usar la página General para cambiar la configuración global del editor de texto y del código de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1665db5fff414227c18fd8de4224302cb6d43c2a
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040607"
---
# <a name="options-dialog-box-text-editor--general"></a>Cuadro de diálogo Opciones: Editor de texto \> General

Este cuadro de diálogo le permite cambiar la configuración global del editor de texto y el código de Visual Studio. Para tener acceso a este cuadro de diálogo, seleccione **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto** y, después, seleccione **General**.

## <a name="settings"></a>Configuración

### <a name="drag-and-drop-text-editing"></a>Editar texto con arrastrar y colocar

Cuando está seleccionada, le permite mover texto seleccionándolo y arrastrándolo con el mouse a otra ubicación dentro del documento actual o en cualquier otro documento abierto.

### <a name="automatic-delimiter-highlighting"></a>Resaltar con el delimitador automático

Cuando está seleccionada, los caracteres de delimitador que separan los parámetros o los pares elemento-valor, así como las llaves coincidentes, se resaltan.

### <a name="track-changes"></a>Control de cambios

Cuando el editor de código está seleccionado, aparece una línea amarilla vertical en el margen de selección para marcar el código que ha cambiado desde que el archivo se guardó por última vez. Cuando guarda los cambios, las líneas verticales se convierten en color verde.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Detectar automáticamente codificación UTF-8 sin firma

De manera predeterminada, el editor detecta la codificación buscando marcas BOM o etiquetas del conjunto de caracteres. Si no se detecta ninguna en el documento actual, el editor de código intenta detectar automáticamente la codificación UTF-8 analizando las secuencias de bytes. Para deshabilitar la detección automática de la codificación, desactive esta opción.

### <a name="follow-project-coding-conventions"></a>Seguir las convenciones de codificación del proyecto

Cuando está activa, las convenciones de la codificación especificada del proyecto reemplazan cualquier convención de codificación que usa en sus proyectos personales.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Habilitar el clic del mouse para Ir a definición

Si se selecciona esta opción, puede presionar **Ctrl** y mantener el puntero sobre un elemento mientras hace clic con el mouse. Al hacerlo, va a la definición del elemento seleccionado. También puede elegir **Alt** o **Ctrl** + **Alt** en el menú desplegable **Usar clave de modificador**.

Active la casilla de verificación **Abrir definición en vista de inspección** para mostrar la definición del elemento en una ventana sin salir de la ubicación actual en el editor de código.

## <a name="display"></a>Pantalla

### <a name="selection-margin"></a>Margen de selección

Cuando está seleccionada, muestra un margen vertical a lo largo del borde izquierdo del área de texto del editor. Puede hacer clic en este margen para seleccionar una línea de texto completa, o hacer clic y arrastrar para seleccionar líneas de texto consecutivas.

|Margen de selección activado|Margen de selección desactivado|
| - | - |
|![Captura de pantalla de HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Captura de pantalla de HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margen del indicador

Cuando está seleccionada, muestra un margen vertical fuera del borde izquierdo del área de texto del editor. Cuando hace clic en este margen, aparecen un icono e información sobre herramientas relacionados con el texto. Por ejemplo, aparecen puntos de interrupción o accesos directos a la lista de tareas en el margen del indicador. La información del margen del indicador no se imprime.

### <a name="highlight-current-line"></a>Resaltar línea actual

Cuando está seleccionada, muestra un cuadro gris alrededor de la línea de código donde se sitúa el cursor.

### <a name="show-structure-guide-lines"></a>Mostrar líneas guía de estructura

Cuando se selecciona esta opción, aparecen líneas verticales en el editor que se alinean con bloques de código estructurado, lo que permite identificar fácilmente los bloques de código individuales.

### <a name="show-file-health-indicator"></a>Mostrar el indicador de estado del archivo

Cuando está activo, se mostrará una barra de indicador de estado del archivo (errores, advertencias) con opciones de limpieza de código en la esquina inferior izquierda del editor.

## <a name="see-also"></a>Vea también

- [Opciones, Editor de texto, Todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md)
- [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opciones, editor de texto, extensión de archivo](../../ide/reference/options-text-editor-file-extension.md)
- [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personalizar el editor](../how-to-change-text-case-in-the-editor.md)
- [Usar IntelliSense](../../ide/using-intellisense.md)
