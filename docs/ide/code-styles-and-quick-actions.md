---
title: "Preferencias de estilo del código de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload: multiple
ms.openlocfilehash: 741df95afdd7c7e8b6f0ba2de75c1465cd35cc97
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. Seleccione **Editor de texto** > **C#** o **Básico** > **Estilo de código** > **General**. Las opciones configuradas en esta ventana se aplican a la máquina local. Cada elemento de la lista mostrará una vista previa de la preferencia cuando se seleccione, como se muestra a continuación.

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** mediante las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguno**, **Sugerencia**, **Advertencia** o **Error**. Si desea habilitar las [Acciones rápidas](../ide/quick-actions.md) para un estilo de código, asegúrese de que el valor **Gravedad** se establece en un valor distinto de **Ninguno**. El icono de bombilla de Acciones rápidas ![pequeño icono de bombilla](media/vs2015_lightbulbsmall.png) aparecerá cuando se utiliza un estilo no preferido, y puede elegir una opción en la lista Acciones rápidas para volver a escribir automáticamente código para el estilo preferido.

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). En este caso, la configuración del archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. El archivo EditorConfig sirve para aplicar y configurar el estilo de codificación de todo el repositorio o proyecto.

## <a name="see-also"></a>Vea también

[Acciones rápidas](../ide/quick-actions.md)  
[Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)