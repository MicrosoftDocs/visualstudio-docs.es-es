---
title: Soluciones y proyectos en Visual Studio
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: fe7db915f2953bf99b9805700e1236d3d79a194a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747631"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio

## <a name="projects"></a>Proyectos

Cuando cree una aplicación, un sitio web, un complemento, etc. en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos de código fuente, iconos, imágenes, archivos de datos, etc., que se compilan en un archivo ejecutable, biblioteca o sitio web. Un proyecto también contiene la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunica.

> [!NOTE]
> No es necesario usar soluciones o proyectos en Visual Studio para editar, compilar y depurar código. Simplemente puede abrir la carpeta que contiene los archivos de código fuente en Visual Studio y empezar la edición. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Un proyecto se define en un archivo XML con una extensión como *.vbproj*, *.csproj* o *.vcxproj*. Este archivo contiene una jerarquía de carpetas virtuales y rutas de acceso a todos los elementos en el proyecto. Además, contiene toda la configuración de compilación.

> [!TIP]
> Para examinar el contenido de un archivo de proyecto en Visual Studio, primero descargue el proyecto al seleccionar el nombre del proyecto en el **Explorador de soluciones** y elegir **Descargar el proyecto** en el menú contextual. Después, vuelva a abrir el menú contextual y elija **Editar \<NombreDelProyecto\>**.

En Visual Studio, el **Explorador de soluciones** usa el archivo de proyecto para mostrar el contenido y la configuración del proyecto. Cuando compila el proyecto, el motor de MSBuild consume el archivo de proyecto para crear el archivo ejecutable. También puede personalizar proyectos para producir otro tipo de resultados.

## <a name="solutions"></a>Soluciones

Un proyecto está incluido dentro de una *solución*. Una solución contiene uno o más proyectos relacionados, junto con información de compilación, la configuración de ventanas de Visual Studio y archivos varios que no estén asociados a un proyecto determinado. Una solución se describe mediante un archivo de texto (extensión *.sln*) con su propio formato único; no está diseñada para modificarse de forma manual.

Una solución tiene un archivo *.suo* asociado que almacena la configuración, las preferencias y la información de configuración de cada usuario que ha trabajado en el proyecto.

## <a name="create-new-projects"></a>Crear nuevos proyectos

La manera más fácil de crear un proyecto consiste en empezar desde una plantilla de proyecto para un tipo concreto de aplicación o sitio web. Una plantilla de proyecto consta de un conjunto básico de archivos de código generados previamente, archivos de configuración, recursos y configuraciones. Estas plantillas son lo que ve en el cuadro de diálogo **Nuevo proyecto** o **Nuevo sitio web** cuando selecciona **Archivo** > **Nuevo** > **Proyecto** o **Archivo** > **Nuevo** > **Sitio web**. Para obtener más información, vea [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md).

También puede crear un proyecto y plantillas de elemento personalizados. Para obtener más información, vea [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Administrar proyectos en el Explorador de soluciones

Después de crear un proyecto nuevo, puede usar el **Explorador de soluciones** para ver y administrar el proyecto, la solución y sus elementos asociados. La siguiente ilustración muestra el **Explorador de soluciones** con una solución de C# que contiene dos proyectos.

![Explorador de soluciones](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>Vea también

- [IDE de Visual Studio](../ide/visual-studio-ide.md)