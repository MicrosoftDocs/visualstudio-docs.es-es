---
title: Soluciones y proyectos en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/5/2017
ms.technology: vs-ide-general
ms.topic: conceptual
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
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11441c826a316d995e75f2b6c79232f19985c17b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio

## <a name="projects"></a>Proyectos

Cuando cree una aplicación, un sitio web, un complemento, etc. en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos de código fuente, iconos, imágenes, archivos de datos, etc., que se compilan en un archivo ejecutable, biblioteca o sitio web. Un proyecto también contiene la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunica.

> [!NOTE]
> No es necesario usar soluciones o proyectos en Visual Studio para editar, compilar y depurar código. Simplemente puede abrir la carpeta que contiene los archivos de código fuente en Visual Studio y empezar la edición. Consulte [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) para obtener más información.

Un proyecto se define en un archivo XML con una extensión como .vbproj, .csproj o .vcxproj. Este archivo contiene una jerarquía de carpetas virtuales y rutas de acceso a todos los elementos en el proyecto. Además, contiene toda la configuración de compilación.

> [!TIP]
> Para examinar el contenido de un archivo de proyecto en Visual Studio, primero descargue el proyecto seleccionando el nombre del proyecto en el Explorador de soluciones y eligiendo **Descargar el proyecto** en el menú contextual. Después, vuelva a abrir el menú contextual y elija **Editar \<NombreDelProyecto\>**.

En Visual Studio, se usa el archivo de proyecto mediante el Explorador de soluciones para mostrar el contenido del proyecto y la configuración. Cuando compila el proyecto, el motor de MSBuild consume el archivo de proyecto para crear el archivo ejecutable. También puede personalizar proyectos para producir otro tipo de resultados.

## <a name="solutions"></a>Soluciones

Un proyecto está incluido dentro de una *solución*. Una solución contiene uno o más proyectos relacionados, junto con información de compilación, la configuración de ventanas de Visual Studio y archivos varios que no estén asociados a un proyecto determinado. Una solución se describe mediante un archivo de texto (con la extensión .sln) con su propio formato único; por lo general no está diseñada para modificarse de forma manual.

Una solución tiene un archivo *.suo* asociado que almacena la configuración, las preferencias y la información de configuración para cada usuario que haya trabajado en el proyecto.

## <a name="creating-new-projects"></a>Crear nuevos proyectos

La manera más fácil de crear un proyecto consiste en empezar desde una plantilla de proyecto para un tipo concreto de aplicación o sitio web. Una plantilla de proyecto consta de un conjunto básico de archivos de código generados previamente, archivos de configuración, recursos y configuraciones. Estas plantillas son lo que ve en el cuadro de diálogo **Nuevo proyecto** o **Nuevo sitio web** cuando selecciona **Archivo**, **Nuevo**, **Proyecto** o **Archivo**, **Nuevo**, **Sitio web**. Para más información, vea [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md).

También puede crear un proyecto y plantillas de elemento personalizados. Para obtener más información, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).

## <a name="managing-projects-in-solution-explorer"></a>Administración de proyectos en el Explorador de soluciones

Después de crear un proyecto nuevo, puede usar el **Explorador de soluciones** para ver y administrar el proyecto, la solución y sus elementos asociados. La siguiente ilustración muestra el Explorador de soluciones con una solución de C# que contiene dos proyectos.

![Explorador de soluciones](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Vea también

[IDE de Visual Studio](../ide/visual-studio-ide.md)
