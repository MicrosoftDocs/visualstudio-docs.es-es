---
title: Procedimiento Especificar un icono de aplicación (Visual Basic, C#)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f2903821c0e0843de43f68d67cc64c344ab95e02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547785"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedimiento Especificar un icono de aplicación (Visual Basic, C#)

La propiedad `Icon` de un proyecto especifica el archivo de icono (*.ico*) que se mostrará para la aplicación compilada en el **Explorador de archivos** y en la barra de tareas de Windows.

Se puede acceder a la propiedad `Icon` desde el panel **Aplicación** del **Diseñador de proyectos**. Contiene una lista de iconos que se han agregado a un proyecto, como recursos o como archivos de contenido.

> [!NOTE]
> Después de establecer la propiedad de icono para una aplicación, también puede establecer la propiedad `Icon` de cada **Ventana** o **Formulario** en la aplicación. Para obtener información acerca de los iconos de la ventana para las aplicaciones independientes de Windows Presentation Foundation (WPF), consulte la propiedad <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar el icono de una aplicación

1. En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).

1. En la barra de menús, seleccione **Proyecto** > **Propiedades**.

1. Cuando aparezca **Diseñador de proyectos**, elija la pestaña **Aplicación**.

1. **(Visual Basic)**&mdash;En la lista **Icono**, elija un archivo de icono (*.ico*).

    **C#**&mdash;Cerca de la lista **Icono**, elija el botón **\<Examinar... >** y, después, vaya a la ubicación del archivo de icono que quiere.

## <a name="see-also"></a>Vea también

- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)