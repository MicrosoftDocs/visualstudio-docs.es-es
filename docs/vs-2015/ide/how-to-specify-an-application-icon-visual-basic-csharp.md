---
title: Procedimiento Especificar un icono de aplicación (Visual Basic, C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f794f1c988215f8899dce495f725b3a9c14a435
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788170"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Cómo: Especificar el icono de una aplicación (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La propiedad `Icon` de un proyecto especifica el archivo de icono (.ico) que se mostrará para la aplicación compilada en el Explorador de archivos y en la barra de tareas de Windows.  
  
 Se puede acceder a la propiedad `Icon` desde el panel **Aplicación** del **Diseñador de proyectos**. Contiene una lista de iconos que se han agregado a un proyecto, como recursos o como archivos de contenido.  
  
> [!NOTE]
>  Después de establecer la propiedad de icono para una aplicación, también puede establecer la propiedad `Icon` de cada **Ventana** o **Formulario** en la aplicación. Para obtener información acerca de los iconos de la ventana para las aplicaciones independientes de Windows Presentation Foundation (WPF), consulte la propiedad <xref:System.Windows.Window.Icon%2A>.  
  
### <a name="to-specify-an-application-icon"></a>Para especificar el icono de una aplicación  
  
1.  En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).  
  
2.  En la barra de menús, seleccione **Proyecto**, **Propiedades**.  
  
3.  Cuando aparezca **Diseñador de proyectos**, elija la pestaña **Aplicación**.  
  
4.  **(Visual Basic)** En la lista **Icono**, elija un archivo de icono (.ico).  
  
     **C#** Cerca de la lista **Icono**, elija el botón **\<Examinar... >** y, después, vaya a la ubicación del archivo de icono que quiere.  
  
## <a name="see-also"></a>Vea también  
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Administrar las propiedades de la aplicación](../ide/application-properties.md)  
 [Cómo: Agregar o quitar recursos](http://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
