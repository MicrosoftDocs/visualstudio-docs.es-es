---
title: Soluciones y proyectos en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio
Cuando cree una aplicación, un sitio web, un complemento, etc. en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos de código fuente, iconos, imágenes, archivos de datos y cualquier otra cosa que se compilará en un programa ejecutable o sitio web, etc. necesarios para realizar la compilación. Un proyecto también contiene toda la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunicará.  

> [!NOTE]
>  No tiene que usar soluciones o proyectos si no quiere. Simplemente, puede abrir los archivos en Visual Studio y comenzar a editar el código. Consulte [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) para obtener más información.  

Un archivo de proyecto (.vbproj, .csproj, .vcxproj) es un archivo XML que define una jerarquía de carpetas virtuales junto con las rutas de acceso a todos los elementos del proyecto. Además, contiene toda la configuración de compilación. Para ver el contenido de un archivo de proyecto, seleccione el nombre del proyecto en el Explorador de soluciones y elija **Descargar el proyecto** en el menú contextual (clic con el botón derecho). Después, vuelva a abrir el menú contextual y elija **Editar \<NombreDelProyecto\>**.  

En Visual Studio, se usa el archivo de proyecto mediante el Explorador de soluciones para mostrar el contenido del proyecto y la configuración. Cuando compila el proyecto, el motor de MSBuild consume el archivo de proyecto para crear el archivo ejecutable. También puede personalizar proyectos para producir otro tipo de resultados.  

Un proyecto está contenido, en un sentido lógico y en el sistema de archivos, en una *solución* que puede incluir uno o más proyectos relacionados, junto con información de compilación, la configuración de ventana de Visual Studio y archivos varios que no estén asociados a ningún proyecto. Una solución se describe mediante un archivo de texto (.sln) con su propio formato único; por lo general no está diseñada para editarse manualmente.  

Una solución tiene un archivo *.suo* asociado que almacena la configuración, las preferencias y la información de configuración para cada usuario que haya trabajado en el proyecto.  

 El siguiente diagrama muestra la relación entre los proyectos y soluciones, y los elementos que estos contienen de forma lógica.  

 ![Soluciones y proyectos de Visual Studio](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Crear nuevos proyectos  
 La manera más fácil de crear un proyecto es empezar con una plantilla de proyecto, que consta de un conjunto básico de archivos de código generados previamente, archivos de configuración, activos y configuraciones que permiten comenzar a crear un tipo concreto de aplicación o sitio web en un lenguaje de programación determinado. Estas plantillas son lo que ve en el cuadro de diálogo **Nuevo proyecto** o **Nuevo sitio web** cuando selecciona **Archivo**, **Nuevo**, **Proyecto** o **Archivo**, **Nuevo**, **Sitio web**. Para más información, vea [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md).  

También puede crear un proyecto y plantillas de elemento personalizados. Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Administración de proyectos en el Explorador de soluciones  
 Después de crear un proyecto nuevo, use el **Explorador de soluciones** para ver y administrar proyectos, soluciones y los elementos que tienen asociados. La siguiente ilustración muestra el Explorador de soluciones con una solución de C# que contiene dos proyectos.  

 ![Explorador de soluciones](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>En esta sección  

-   [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md)  

-   [Agregar y quitar elementos del proyecto](../ide/adding-and-removing-project-items.md)  

-   [Administrar propiedades de soluciones y proyectos](../ide/managing-project-and-solution-properties.md)  

-   [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)  

-   [Propiedades de la aplicación](../ide/application-properties.md)  

-   [Administrar la firma de ensamblados y manifiestos](../ide/managing-assembly-and-manifest-signing.md)  

-   [Cómo: Especificar el icono de una aplicación (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Vea también  
 [IDE de Visual Studio](../ide/visual-studio-ide.md)
