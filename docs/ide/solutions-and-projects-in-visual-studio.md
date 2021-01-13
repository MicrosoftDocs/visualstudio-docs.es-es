---
title: Más información sobre soluciones y proyectos
description: Vea cómo son los proyectos y las soluciones de Visual Studio, cómo se crean proyectos nuevos a partir de una plantilla y cómo se pueden ver y administrar los proyectos en el Explorador de soluciones.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b34d96f49370a71a63e986a79584caffbc00adf
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847038"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluciones y proyectos en Visual Studio

En esta página se explica el concepto de *proyecto* y *solución* en Visual Studio. También se trata brevemente la ventana de la herramienta Explorador de soluciones y cómo crear un proyecto.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Proyectos y soluciones en Visual Studio para Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Proyectos

Cuando cree una aplicación o un sitio web en Visual Studio, debe comenzar con un *proyecto*. En un sentido lógico, un proyecto contiene todos los archivos que se compilan en un archivo ejecutable, biblioteca o sitio web. Estos archivos pueden incluir código fuente, iconos, imágenes, archivos de datos, etc. Un proyecto también contiene la configuración del compilador y otros archivos de configuración que podrían ser necesarios en diversos servicios o componentes con los que el programa se comunica.

### <a name="project-file"></a>Archivo del proyecto

Visual Studio usa [MSBuild](../msbuild/msbuild.md) para compilar cada proyecto en una solución, y cada proyecto contiene un archivo de proyecto de MSBuild. La extensión de archivo refleja el tipo de proyecto, por ejemplo, un proyecto de C# (.csproj), un proyecto de Visual Basic (.vbproj) o un proyecto de base de datos (.dbproj). El archivo de proyecto es un documento XML que contiene toda la información y las instrucciones que MSBuild necesita para compilar el proyecto, incluidos el contenido, los requisitos de la plataforma, la información de versión, la configuración del servidor web o del servidor de bases de datos y las tareas que se deben llevar a cabo.

Los archivos de proyecto se basan en el [esquema XML de MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Para ver el contenido de los [archivos de proyecto de estilo SDK](../msbuild/how-to-use-project-sdk.md) más recientes en Visual Studio, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Editar \<projectname\>** . Para ver el contenido de proyectos de .NET Framework y otros del estilo, descargue primero el proyecto (haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Descargar el proyecto**). Después, haga clic con el botón derecho en el proyecto y seleccione **Editar \<projectname\>** .

> [!NOTE]
> No es necesario usar soluciones o proyectos en Visual Studio para editar, compilar y depurar código. Simplemente puede abrir la carpeta que contiene los archivos de código fuente en Visual Studio y empezar la edición. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="create-new-projects"></a>Crear nuevos proyectos

La forma más fácil de crear un nuevo proyecto es usar una plantilla de proyecto para el tipo de proyecto que quiera. Una plantilla de proyecto incluye un conjunto básico de archivos de código generados previamente, archivos de configuración, recursos y configuraciones. Vaya a **Archivo** > **Nuevo** > **Proyecto** para seleccionar una plantilla de proyecto. Para obtener más información, vea [Creación de un proyecto en Visual Studio](create-new-project.md).

También puede crear una plantilla de proyecto personalizada que puede usar para crear nuevos proyectos. Para obtener más información, vea [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md).

Cuando se crea un nuevo proyecto, Visual Studio lo guarda en su ubicación predeterminada, *%USERPROFILE%\source\repos*. Para cambiar esta ubicación, vaya a **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Ubicaciones**. Para obtener más información, vea [Cuadro de diálogo Opciones: Proyectos y soluciones > Ubicaciones](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Soluciones

Un proyecto está incluido dentro de una *solución*. A pesar de su nombre, una solución no es una "respuesta", sino simplemente un contenedor con uno o más proyectos relacionados, junto con información de compilación, la configuración de ventanas de Visual Studio y archivos varios que no estén asociados a un proyecto determinado.

### <a name="solution-file"></a>Archivo de soluciones

En Visual Studio se usan dos tipos de archivo ( *.sln* y *.suo*) para almacenar la configuración de las soluciones:

|Comprobación de actualización|NOMBRE|Descripción|
|---------------|----------|-----------------|
|.sln|Solución de Visual Studio|Organiza proyectos, elementos de proyecto y elementos de solución en la solución.|
|.suo|Opciones de usuario de la solución|Almacena la configuración de nivel de usuario y las personalizaciones, como los puntos de interrupción.|

> [!IMPORTANT]
> Una solución se describe mediante un archivo de texto (extensión *.sln*) con su propio formato único; no está diseñada para modificarse de forma manual. Por otro lado, el archivo *.suo* es un archivo oculto que no aparece en la configuración predeterminada del Explorador de archivos. Para mostrar los archivos ocultos, en el menú **Vista** del Explorador de archivos, seleccione la casilla **Elementos ocultos**.

### <a name="solution-folder"></a>Carpeta de solución

Una "carpeta de solución" es una carpeta virtual que solo se encuentra en el **Explorador de soluciones**, donde se puede usar para agrupar proyectos en una solución. Si desea buscar un archivo de una solución en un equipo, vaya a **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Ubicaciones**. Para obtener más información, vea [Cuadro de diálogo Opciones: Proyectos y soluciones > Ubicaciones](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Para obtener un ejemplo de un proyecto y una solución creados desde cero con instrucciones paso a paso y código de ejemplo, vea [Información sobre proyectos y soluciones](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Explorador de soluciones

Después de crear un proyecto nuevo, puede usar el **Explorador de soluciones** para ver y administrar el proyecto, la solución y sus elementos asociados. En la siguiente ilustración se muestra el **Explorador de soluciones** con una solución de C# que contiene dos proyectos:

::: moniker range="vs-2017"

![Captura de pantalla del Explorador de soluciones con dos proyectos.](../ide/media/vs2015_solution_explorer.png)

La barra de herramientas de la parte superior del **Explorador de soluciones** tiene botones para cambiar de una vista de solución a una vista de carpeta, mostrar archivos ocultos, contraer todos los nodos y mucho más.

::: moniker-end

::: moniker range="vs-2019"

![Captura de pantalla del Explorador de soluciones con dos proyectos en Visual Studio 2019.](../ide/media/solution-explorer.png)

La barra de herramientas situada en la parte superior del **Explorador de soluciones** tiene botones para cambiar de una vista de solución a una vista de carpeta, filtrar los cambios pendientes, mostrar todos los archivos, contraer todos los nodos, ver las páginas de [propiedades](managing-project-and-solution-properties.md), obtener una vista previa del código en el [editor de código](writing-code-in-the-code-and-text-editor.md), etc.

::: moniker-end

Muchos comandos de menú están disponibles en el menú contextual que aparece al hacer clic con el botón derecho en distintos elementos del **Explorador de soluciones**. Estos comandos incluyen compilar un proyecto, administrar paquetes NuGet, agregar una referencia, cambiar el nombre de un archivo y ejecutar pruebas, solo por nombrar algunos.

> [!TIP]
> Si ha cerrado el Explorador de soluciones y quiere volver a abrirlo, elija **Ventana** > **Restablecer diseños de ventana** en la barra de menús.

Para los proyectos de ASP.NET Core, puede personalizar cómo se anidan los archivos en el **Explorador de soluciones**. Para obtener más información, consulte [Personalizar el anidamiento de archivos en el Explorador de soluciones](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Consulte también

- [Introducción a proyectos y soluciones](../get-started/tutorial-projects-solutions.md)
- [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)
- [Soluciones filtradas en Visual Studio](filtered-solutions.md)
- [Portar, migrar y actualizar proyectos](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Recursos para solucionar problemas de errores en el entorno de desarrollo integrado](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Proyectos y soluciones (Visual Studio para Mac)](/visualstudio/mac/projects-and-solutions)