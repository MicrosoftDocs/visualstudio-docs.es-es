---
title: "C&#243;mo: Especificar el icono de una aplicaci&#243;n (Visual Basic, C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "iconos [Visual Studio], aplicación"
  - "propiedades de aplicación [Visual Studio], iconos"
  - "iconos de aplicación [Visual Studio]"
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Cómo: Especificar el icono de una aplicación (Visual Basic, C#)
La propiedad `Icon` de un proyecto especifica el archivo de icono (.ico) que se mostrará para la aplicación compilada en el Explorador de archivos y en la barra de tareas de Windows.  
  
 Se puede acceder a la propiedad `Icon` desde el panel **Aplicación** del **Diseñador de proyectos**. Contiene una lista de iconos que se han agregado a un proyecto, como recursos o como archivos de contenido.  
  
> [!NOTE]
>  Después de establecer la propiedad de icono para una aplicación, también puede establecer la propiedad `Icon` de cada **Ventana** o **Formulario** en la aplicación. Para obtener información sobre los iconos de la ventana para las aplicaciones independientes de Windows Presentation Foundation (WPF), vea la propiedad <xref:System.Windows.Window.Icon%2A>.  
  
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


<!--HONumber=Feb17_HO4-->


