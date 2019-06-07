---
title: Soluciones y proyectos
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42a8dbc2fd9a6fc89b0be62271b048f8275a82b2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432200"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio

En este artículo se explica el concepto de *proyecto* y *solución* en Visual Studio. También se trata brevemente cómo crear un proyecto y la ventana de la herramienta **Explorador de soluciones**.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Proyectos y soluciones en Visual Studio para Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Proyectos

Cuando cree una aplicación, un sitio web, un complemento, etc. en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos de código fuente, iconos, imágenes, archivos de datos, etc., que se compilan en un archivo ejecutable, biblioteca o sitio web. Un proyecto también contiene la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunica.

> [!NOTE]
> No es necesario usar soluciones o proyectos en Visual Studio para editar, compilar y depurar código. Simplemente puede abrir la carpeta que contiene los archivos de código fuente en Visual Studio y empezar la edición. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Un proyecto se define en un archivo XML con una extensión como *.vbproj*, *.csproj* o *.vcxproj*. Este archivo contiene una jerarquía de carpetas virtuales y rutas de acceso a todos los elementos en el proyecto. Además, contiene toda la configuración de compilación.

> [!TIP]
> Para examinar el contenido de un archivo de proyecto en Visual Studio, primero descargue el proyecto al seleccionar el nombre del proyecto en el **Explorador de soluciones** y elegir **Descargar el proyecto** en el menú contextual. Después, vuelva a abrir el menú contextual y elija **Editar \<NombreDelProyecto\>** .

En Visual Studio, el **Explorador de soluciones** usa el archivo de proyecto para mostrar el contenido y la configuración del proyecto. Cuando compila el proyecto, el motor de MSBuild consume el archivo de proyecto para crear el archivo ejecutable. También puede personalizar proyectos para producir otro tipo de resultados.

## <a name="solutions"></a>Soluciones

Un proyecto está incluido dentro de una *solución*. A pesar de su nombre, una solución no es una "respuesta", sino simplemente un contenedor con uno o más proyectos relacionados, junto con información de compilación, la configuración de ventanas de Visual Studio y archivos varios que no estén asociados a un proyecto determinado. Una solución se describe mediante un archivo de texto (extensión *.sln*) con su propio formato único; no está diseñada para modificarse de forma manual.

En Visual Studio se usan dos tipos de archivo ( *.sln* y *.suo*) para almacenar la configuración de las soluciones:

|Comprobación de actualización|nombre|Descripción|
|---------------|----------|-----------------|
|.sln|Solución de Visual Studio|Organiza proyectos, elementos de proyecto y elementos de solución en la solución.|
|.suo|Opciones de usuario de la solución|Almacena la configuración de nivel de usuario y las personalizaciones, como los puntos de interrupción.|

## <a name="create-new-projects"></a>Crear nuevos proyectos

La manera más fácil de crear un proyecto consiste en empezar desde una plantilla de proyecto para un tipo concreto de aplicación o sitio web. Una plantilla de proyecto consta de un conjunto básico de archivos de código generados previamente, archivos de configuración, recursos y configuraciones. Estas plantillas están disponibles en el cuadro de diálogo en que se crea un proyecto (**Archivo** > **Nuevo** > **Proyecto**). Para obtener más información, consulte [Creación de un proyecto nuevo en Visual Studio](create-new-project.md) y [Crear soluciones y proyectos](../ide/creating-solutions-and-projects.md).

Si a menudo personaliza sus proyectos de una determinada manera, puede crear una plantilla de proyecto personalizada que luego puede usar para crear nuevos proyectos. Para obtener más información, vea [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md).

Cuando crea un proyecto, se guarda de forma predeterminada en *%USERPROFILE%\source\repos*. Puede cambiar esta ubicación en el ajuste **Ubicación del proyecto**, que encontrará en **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Ubicaciones**. Para obtener más información, vea [Página Proyectos y soluciones, Cuadro de diálogo Opciones](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Explorador de soluciones

Después de crear un proyecto nuevo, puede usar el **Explorador de soluciones** para ver y administrar el proyecto, la solución y sus elementos asociados. En la siguiente ilustración se muestra el **Explorador de soluciones** con una solución de C# que contiene dos proyectos:

![Explorador de soluciones](../ide/media/vs2015_solution_explorer.png)

Muchos comandos de menú están disponibles en el menú que aparece al hacer clic derecho en distintos elementos del **Explorador de soluciones**. Estos comandos incluyen compilar un proyecto, administrar paquetes NuGet, agregar una referencia, cambiar el nombre de un archivo y ejecutar pruebas, solo por nombrar algunos. La barra de herramientas de la parte superior del **Explorador de soluciones** tiene botones para cambiar de una vista de solución a una vista de carpeta, mostrar archivos ocultos, contraer todos los nodos y mucho más.

Para los proyectos de ASP.NET Core, puede personalizar cómo se anidan los archivos en el **Explorador de soluciones**. Para obtener más información, consulte [Personalizar el anidamiento de archivos en el Explorador de soluciones](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Vea también

- [IDE de Visual Studio](../get-started/visual-studio-ide.md)
- [Proyectos y soluciones (Visual Studio para Mac)](/visualstudio/mac/projects-and-solutions)
- [Agregar y quitar elementos del proyecto (Visual Studio para Mac)](/visualstudio/mac/add-and-remove-project-items)
