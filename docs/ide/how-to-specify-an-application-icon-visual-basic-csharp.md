---
title: "Cómo: Especificar el icono de una aplicación (Visual Basic, C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3309b02a50f3f14d166044c2d1cea35bdab3922f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Cómo: Especificar el icono de una aplicación (Visual Basic, C#)

La propiedad `Icon` de un proyecto especifica el archivo de icono (.ico) que se mostrará para la aplicación compilada en el Explorador de archivos y en la barra de tareas de Windows.

Se puede acceder a la propiedad `Icon` desde el panel **Aplicación** del **Diseñador de proyectos**. Contiene una lista de iconos que se han agregado a un proyecto, como recursos o como archivos de contenido.

> [!NOTE]
> Después de establecer la propiedad de icono para una aplicación, también puede establecer la propiedad `Icon` de cada **Ventana** o **Formulario** en la aplicación. Para obtener información acerca de los iconos de la ventana para las aplicaciones independientes de Windows Presentation Foundation (WPF), consulte la propiedad <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar el icono de una aplicación

1. En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).

1. En la barra de menús, seleccione **Proyecto** > **Propiedades**.

1. Cuando aparezca **Diseñador de proyectos**, elija la pestaña **Aplicación**.

1. **(Visual Basic)**&mdash;En la lista **Icono**, elija un archivo de icono (.ico).

    **C#**&mdash;Cerca de la lista **Icono**, elija el botón **\<Examinar... >** y, después, vaya a la ubicación del archivo de icono que quiere.

## <a name="see-also"></a>Vea también

[Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)
