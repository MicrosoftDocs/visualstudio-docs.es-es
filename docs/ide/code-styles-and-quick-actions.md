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
ms.openlocfilehash: 80b7260296f1f57448ae94147a59dbb29160be40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="code-style-preferences"></a>Preferencias de estilo del código

Para establecer las preferencias de estilo del código de los proyectos de C# y Visual Basic, abra el cuadro de diálogo **Opciones** desde el menú **Herramientas**. Seleccione **Editor de texto**, **C#** o **Basic**, **Estilo de código**, **General**. Las opciones configuradas en esta ventana se aplican a la máquina local. Cada elemento de la lista mostrará una vista previa de la preferencia cuando se seleccione, como se muestra a continuación.

![Opciones de estilo de código](media/code-style-quick-actions-dialog.png)

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** mediante las listas desplegables de cada línea. La gravedad se puede establecer en **Ninguna**, **Sugerencia**, **Advertencia** o **Error**, y Visual Studio se comportará de la forma correspondiente. Si quiere usar las [acciones rápidas](quick-actions.md) con estos estilos de código para escribir el código automáticamente con el estilo preferido, asegúrese de que la gravedad esté establecida en un valor diferente de **Ninguna**, de modo que el icono de bombilla ![icono de bombilla pequeño](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") aparezca cuando se usan los estilos no preferidos. Para aplicar estas preferencias, haga clic en el icono de bombilla o pulse **Ctrl + .** cuando el cursor esté en la línea de código adecuada.

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). En este caso, la configuración del archivo EditorConfig tiene prioridad sobre las opciones seleccionadas en el cuadro de diálogo **Opciones**. El archivo EditorConfig sirve para aplicar y configurar el estilo de codificación de todo el repositorio o proyecto.

## <a name="see-also"></a>Vea también

[Acciones rápidas](quick-actions.md)  
[Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)