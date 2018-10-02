---
title: 'Cómo: Especificar el icono de una aplicación (Visual Basic, C#) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d696766d2dd32ada86d74754dce87320e8f1627
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582356"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Cómo: Especificar el icono de una aplicación (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: especificar un icono de aplicación (Visual Basic, C#)](https://docs.microsoft.com/visualstudio/ide/how-to-specify-an-application-icon-visual-basic-csharp).  
  
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
 [Cómo: Agregar o quitar recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)



