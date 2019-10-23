---
title: Procedimiento Especificar un icono de aplicación (Visual Basic, C#)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1e137eda77f1807b80409872d9fe0c2966df2a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656603"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procedimiento Especificar un icono de aplicación (Visual Basic, C#)

La propiedad `Icon` de un proyecto especifica el archivo de icono ( *.ico*) que se mostrará para la aplicación compilada en el **Explorador de archivos** y en la barra de tareas de Windows.

Se puede acceder a la propiedad `Icon` desde el panel **Aplicación** del **Diseñador de proyectos**. Contiene una lista de iconos que se han agregado a un proyecto, como recursos o como archivos de contenido.

> [!NOTE]
> Después de establecer la propiedad de icono para una aplicación, también puede establecer la propiedad `Icon` de cada **Ventana** o **Formulario** en la aplicación. Para obtener información acerca de los iconos de la ventana para las aplicaciones independientes de Windows Presentation Foundation (WPF), consulte la propiedad <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar el icono de una aplicación

1. En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).

1. En la barra de menús, seleccione **Proyecto** > **Propiedades**.

1. Cuando aparezca **Diseñador de proyectos**, elija la pestaña **Aplicación**.

1. **(Visual Basic)** &mdash;En la lista **Icono**, elija un archivo de icono ( *.ico*).

    **C#** &mdash;Cerca de la lista **Icono**, elija el botón **\<Examinar... >** y, después, vaya a la ubicación del archivo de icono que quiere.

## <a name="see-also"></a>Vea también

- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)