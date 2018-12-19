---
title: Soluciones y proyectos
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 068fe27df565f83312040fa0bcf6412e4984d9fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067147"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando cree una aplicación, una solicitud, un sitio web, una aplicación web, un script, un complemento, etc. en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos de código fuente, iconos, imágenes, archivos de datos y cualquier otra cosa que se compilará en un programa ejecutable o sitio web, etc. necesarios para realizar la compilación.  Un proyecto también contiene toda la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunicará.

 En un sentido literal, un proyecto es un archivo XML (*.vbproj, \*.csproj, \*.vcxproj) que define una jerarquía de carpetas virtuales junto con las rutas de acceso a todos los elementos que contiene y a toda la configuración de compilación. En Visual Studio, se usa el archivo de proyecto mediante el Explorador de soluciones para mostrar el contenido del proyecto y la configuración. Cuando compila el proyecto, el motor de MSBuild consume el archivo de proyecto para crear el archivo ejecutable. También puede personalizar proyectos para producir otro tipo de resultados.

 Un proyecto se encuentra, en un sentido lógico y en el sistema de archivos, en una *solución*que puede contener uno o más proyectos, junto con información de compilación, la configuración de ventana de Visual Studio y archivos varios que no estén asociados a ningún proyecto. En un sentido literal, la solución es un archivo de texto con su propio formato único; por lo general no está diseñada para editarse manualmente.

 Una solución tiene un archivo *.suo asociado que almacena la configuración, las preferencias y la información de configuración para cada usuario que haya trabajado en el proyecto.

 El siguiente diagrama muestra la relación entre los proyectos y soluciones, y los elementos que estos contienen de forma lógica.

 ![Soluciones y proyectos de Visual Studio](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 También puede crear un proyecto y plantillas de elemento personalizados. Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Crear nuevos proyectos
 La manera más fácil de crear un nuevo proyecto es empezar con una plantilla de proyecto predefinida, que consiste en un conjunto básico de archivos de código generados previamente, archivos de configuración, activos y configuraciones que permiten comenzar a crear un tipo concreto de aplicación o sitio web en un lenguaje de programación determinado. Estas plantillas son las que puede ver en el **cuadro de diálogo Nuevo proyecto** cuando selecciona **Archivo &#124; Nuevo &#124; Proyecto** o **Archivo &#124; Nuevo &#124; Sitio web** en el menú principal y navega por él. Para obtener más información, vea [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md) y [NIB: Crear proyectos a partir de plantillas](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Administración de proyectos en el Explorador de soluciones
 Después de crear un proyecto nuevo, use el **Explorador de soluciones** para ver y administrar proyectos, soluciones y los elementos que tienen asociados. La siguiente ilustración muestra el Explorador de servidores con una solución de C# que contiene dos proyectos.

 ![Explorador de soluciones](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>En esta sección

-   [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md)

-   [Agregar y quitar elementos del proyecto](../ide/adding-and-removing-project-items.md)

-   [Administrar propiedades de soluciones y proyectos](../ide/managing-project-and-solution-properties.md)

-   [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)

-   [Administrar las propiedades de la aplicación](../ide/application-properties.md)

-   [Administrar la firma de ensamblados y manifiestos](../ide/managing-assembly-and-manifest-signing.md)

-   [Cómo: especificar un icono de aplicación (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

-   [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

-   [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Vea también
 [IDE de Visual Studio](../ide/visual-studio-ide.md)
