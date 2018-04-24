---
title: Opciones, editor de texto, C#, formato | Microsoft Docs
ms.date: 02/09/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: db7140248818cc92f95150e7a368fa0f71d1d010
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-c-formatting"></a>Opciones, editor de texto, C#, formato

Use la página de opciones **Formato** para establecer las opciones de formato de código en el Editor de código. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#** > **Estilo de código** > **Formato**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-settings"></a>Configuración general

La configuración general afecta a la manera en que el Editor de código aplica las opciones de formato al código.

## <a name="uielement-list"></a>Lista de UIElement

|Etiqueta|Description|
|-----------|-----------------|
|**Dar formato automáticamente al escribir**|Si está desactivada, las opciones **Dar formato automáticamente a la instrucción al introducir ;** y **Dar formato automáticamente al bloque al introducir }** están desactivadas.|
|**Dar formato automáticamente a la instrucción al introducir ;**|Si está activada, da formato a las instrucciones a su finalización según las opciones de formato seleccionadas para el editor.|
|**Dar formato automáticamente al bloque al introducir }**|Si está activada, da formato a los bloques de código según las opciones de formato seleccionadas para el editor de código tan pronto como complete el bloque de código.|
|**Dar formato automáticamente al volver**|Si está activada, da formato al texto cuando se presiona **Entrar** para ajustarlo a las opciones de formato seleccionadas para el editor.|
|**Dar formato automáticamente al pegar**|Si está activada, da formato al texto pegado en el editor para ajustarlo a las opciones de formato seleccionadas para el editor.|

## <a name="preview-window"></a>Ventana Vista previa

Los panales de opciones **Sangría**, **Nuevas líneas**, **Espaciado** y **Ajuste** muestran una ventana de vista previa. La ventana de vista previa muestra el efecto de cada opción. Para usar la ventana de vista previa, seleccione una opción de formato. La ventana de vista previa muestra un ejemplo de la opción seleccionada. Cuando cambia la configuración (activando o desactivando una casilla o un botón de radio), la ventana de vista previa se actualiza para mostrar el efecto de la nueva configuración.

## <a name="remarks"></a>Comentarios

Las opciones de sangría de las páginas **Pestañas** de cada idioma solo determinan dónde coloca el cursor el Editor de código cuando presiona **Entrar** al final de una línea. Las opciones de sangría en **Formato** se aplican cuando se da formato al código automáticamente, por ejemplo, cuando pega código en el archivo con la opción **Ajustar sangría al pegar** seleccionada, y cuando el bloque al que se está dando formato se escribe manualmente.

## <a name="see-also"></a>Vea también

[General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
