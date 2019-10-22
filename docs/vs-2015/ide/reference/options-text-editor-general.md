---
title: Opciones, editor de texto, general | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662262"
---
# <a name="options-text-editor-general"></a>Opciones, editor de texto, general
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este cuadro de diálogo le permite cambiar la configuración global del editor de texto y el código de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto** y, después, haga clic en **General**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Configuración
 Arrastrar y colocar edición de texto cuando se selecciona, permite mover texto seleccionándolo y arrastrándolo con el mouse hasta otra ubicación del documento actual o de cualquier otro documento abierto.

 El resaltado automático de delimitadores cuando se selecciona, se resaltan los caracteres delimitadores que separan los parámetros o pares de elemento-valor, así como las llaves coincidentes.

 Seguimiento de cambios cuando se selecciona el editor de código, aparece una línea amarilla vertical en el margen de selección para marcar el código que ha cambiado desde la última vez que se guardó el archivo. Cuando guarda los cambios, las líneas verticales se convierten en color verde.

 Detección automática de la codificación UTF-8 sin signatura de forma predeterminada, el editor detecta la codificación buscando marcas de orden de bytes o etiquetas de juego de caracteres. Si no se detecta ninguna en el documento actual, el editor de código intenta detectar automáticamente la codificación UTF-8 analizando las secuencias de bytes. Para deshabilitar la detección automática de la codificación, desactive esta opción.

## <a name="display"></a>Pantalla
 Margen de selección cuando se selecciona, muestra un margen vertical a lo largo del borde izquierdo del área de texto del editor. Puede hacer clic en este margen para seleccionar una línea de texto completa, o hacer clic y arrastrar para seleccionar líneas de texto consecutivas.

|Margen de selección activado|Margen de selección desactivado|
|-------------------------|--------------------------|
|![Captura de pantalla de HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "|::ref1::|")|![Captura de pantalla de HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "|::ref2::|")|

 Margen del indicador cuando se selecciona, muestra un margen vertical fuera del borde izquierdo del área de texto del editor. Cuando hace clic en este margen, aparecen un icono e información sobre herramientas relacionados con el texto. Por ejemplo, aparecen puntos de interrupción o accesos directos a la lista de tareas en el margen del indicador. La información del margen del indicador no se imprime.

 Barra de desplazamiento vertical cuando está seleccionada, muestra una barra de desplazamiento vertical que le permite desplazarse hacia arriba y hacia abajo para ver los elementos que se encuentran fuera del área de visualización del editor. Si las barras de desplazamiento verticales no están disponibles, puede usar las teclas de dirección, la tecla Retroceder Página y la tecla Avanzar Página para desplazarse.

 Barra de desplazamiento horizontal cuando está seleccionada, muestra una barra de desplazamiento horizontal que le permite desplazarse de lado a lado para ver los elementos que se encuentran fuera del área de visualización del editor. Si las barras de desplazamiento horizontales no están disponibles, puede usar las teclas de dirección para desplazarse.

 Resaltar la línea actual cuando se selecciona, muestra un cuadro gris alrededor de la línea de código en la que se encuentra el cursor.

## <a name="see-also"></a>Otras referencias
 Opciones [, editor de texto, opciones de todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md) [, editor de texto, todos los lenguajes](../../ide/reference/options-text-editor-all-languages-tabs.md) , [Opciones de tabulaciones, editor de texto, extensión de archivo](../../ide/reference/options-text-editor-file-extension.md) [identificación y personalización de métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [personalizar el editor](../../ide/customizing-the-editor.md) [mediante IntelliSense](../../ide/using-intellisense.md)
