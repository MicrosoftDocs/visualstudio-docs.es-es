---
title: "Estilos de código y acciones rápidas | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>Estilos de código y acciones rápidas
Para establecer preferencias de estilo de código para los proyectos de C# y Visual Basic, abra la ventana **Herramientas > Opciones** y, después, seleccione **Editor de texto > C# / Basic > Estilo de código > General**.  Las opciones configuradas en esta ventana se aplican a la máquina local.  Cada elemento de la lista mostrará una vista previa de la preferencia cuando se seleccione, como se muestra a continuación.

![Opciones de estilo de código](~/ide/media/code-style-quick-actions-dialog.png)

Para cada elemento, puede establecer el valor de **Preferencia** y **Gravedad** mediante las listas desplegables de cada línea.  La gravedad se puede establecer en **Ninguna**, **Sugerencia**, **Advertencia** o **Error**, y Visual Studio se comportará de la forma correspondiente.  Si quiere usar las [acciones rápidas](quick-actions.md) con estos estilos de código para escribir el código automáticamente con el estilo preferido, asegúrese de que la gravedad esté establecida en un valor diferente de **Ninguna**, de modo que el icono de bombilla ![icono de bombilla pequeño](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") aparezca cuando se usan los estilos no preferidos.  Para aplicar estas preferencias, haga clic en el icono de bombilla o pulse **Ctrl + .** cuando el cursor esté en la línea de código adecuada.

También puede administrar la configuración del estilo de código para .NET con un archivo [EditorConfig](editorconfig-code-style-settings-reference.md).  En este caso, la configuración seleccionada en la ventana Opciones será la configuración de reserva y el archivo EditorConfig tendrá prioridad.  Puede usar este archivo para aplicar y configurar el estilo de codificación para todo el repositorio o equipo.

# <a name="see-also"></a>Vea también
* [Acciones rápidas](quick-actions.md)
