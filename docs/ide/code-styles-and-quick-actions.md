---
title: Preferencias de estilo del código de Visual Studio
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
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. Seleccione **Editor de texto** > **C#** o **Básico** > **Estilo de código** > **General**. Las opciones configuradas en esta ventana se aplican a la máquina local.

Cada elemento de la lista muestra una vista previa de la preferencia cuando se selecciona:

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>Preferencia y gravedad

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** usando las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguno**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Ninguno**. El icono de bombilla de Acciones rápidas ![icono de bombilla pequeña](media/vs2015_lightbulbsmall.png) aparece cuando se usa un estilo no preferido y puede elegir una opción en la lista Acciones rápidas para volver a escribir código automáticamente para el estilo preferido.

## <a name="editorconfig-files"></a>Archivos EditorConfig

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). La configuración del archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. El archivo EditorConfig sirve para aplicar y configurar el estilo de codificación de todo el repositorio o proyecto.

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)