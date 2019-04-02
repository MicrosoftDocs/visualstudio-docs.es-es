---
title: Proyectos de R
description: Describe cómo crear un administrador de proyectos de R en Visual Studio que incluyan propiedades, comandos de proyecto y plantillas.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 157617ae085a5d298b1e552d0280b98f63e1fc0b
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324791"
---
# <a name="create-r-projects-in-visual-studio"></a>Crear proyectos de R en Visual Studio

Un proyecto de R (un archivo *.rxproj*) identifica los archivos de origen y contenido asociados con el proyecto. También contiene información de compilación de cada archivo, mantiene la información para integrarse con sistemas de control de código fuente y ayuda a organizar la aplicación en componentes lógicos. En cambio, la información relacionada con el área de trabajo, como la lista de paquetes instalados, se mantiene por separado en el área de trabajo.

Los proyectos se administran siempre dentro de una *solución* de Visual Studio, que puede contener cualquier número de proyectos que pueden hacerse referencia entre sí. Vea [Usar varios tipos de proyectos en Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Crear un proyecto de R

1. Abra Visual Studio.
1. Elija **Archivo > Nuevo > Proyecto** (**Ctrl**+**Shift**+**N**).
1. Seleccione "Proyecto de R" en **Plantillas** > **R**, asigne un nombre y una ubicación al proyecto y haga clic en **Aceptar**:

    ![Cuadro de diálogo Nuevo proyecto de R en Visual Studio (RTVS en VS2017)](media/getting-started-01-new-project.png)

Este comando crea un proyecto con un archivo *script.R* vacío abierto en el editor. Tenga en cuenta también que en el **Explorador de soluciones** hay otros dos archivos en el proyecto:

![Contenido de un proyecto de R creado a partir de la plantilla](media/projects-template-results.png)

*.Rhistory* registra todos los comandos que escriba en la ventana [R interactivo](interactive-repl-for-r-in-visual-studio.md). Puede abrir una ventana de historial dedicada con el comando **Herramientas de R** > **Ventanas** > **Historial**. Esta ventana tiene un botón de la barra de herramientas y elementos de menú contextuales para borrar el contenido del historial.

El archivo *rproject.rproj* mantiene determinadas opciones del proyecto específicas de R que, de lo contrario, no se administran en Visual Studio:

| Propiedad. | Default | Descripción |
| --- | --- | --- |
| Versión | 1.0 | La versión de Herramientas de R para Visual Studio usada para crear el proyecto. |
| RestoreWorkspace | Default | Se cargan de forma automática las variables anteriores del área de trabajo desde el archivo `.RData` en el directorio del proyecto. |
| SaveWorkspace | Default | Se guardan las variables actuales del área de trabajo en el archivo `.RData` en el directorio del proyecto al cerrar un proyecto. |
| AlwaysSaveHistory | Default | Se guarda el historial de la ventana interactiva en el archivo `.RHistory` en el directorio del proyecto al cerrar un proyecto. |
| EnableCodeIndexing | Sí | Se determina si se ejecuta una tarea de indexación en segundo plano para acelerar las búsquedas de código. |
| UseSpacesForTab | Sí | Se determina si se insertan espacios (Sí) o un carácter de tabulación (No) cuando se presiona la tecla **Tab** en el editor. |
| NumSpacesForTab | 2 | El número de espacios que se insertan si UseSpacesForTab es Sí. |
| Codificación | UTF-8 | La codificación predeterminada de los archivos `.R`. |
| RnwWeave | Sweave | Paquete que se usará al entretejer un archivo Rnw. |
| LaTeX | pdfLaTeX | Biblioteca que se usará al convertir RMarkdwon a PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Convertir una carpeta de archivos en un proyecto de R

Si dispone de una carpeta existente de archivos *.R* que quiera administrar en un proyecto, siga los pasos siguientes:

1. Cree un proyecto en Visual Studio, como se muestra en la sección anterior.
1. Copie los archivos en la carpeta del proyecto.
1. En el Explorador de soluciones de Visual Studio, haga clic con el botón derecho en el proyecto, seleccione **Agregar** > **Elemento existente** y busque los archivos que quiera agregar. Esos archivos aparecen en el árbol del proyecto después de seleccionar **Aceptar**.
1. Para organizar el código en subcarpetas, haga clic con el botón derecho en el proyecto, seleccione **Agregar** > **Nueva carpeta** en primer lugar, después copie los archivos en esa carpeta y agregue los elementos existentes del paso 3.

## <a name="project-properties"></a>Propiedades del proyecto

Para abrir las páginas de propiedades del proyecto, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades**, o bien seleccione el elemento de menú **Proyecto > Propiedades de (nombre del proyecto)**. La ventana que se abre muestra propiedades del proyecto:


| Tab | Propiedad. | Descripción |
| --- | --- | --- |
| Run | Archivo de inicio | El nombre del archivo que se ejecuta con el comando **Archivo de inicio de origen**, **F5**, **Depurar** > **Iniciar depuración** o **Depurar** > **Iniciar sin depurar**. También puede establecerlo como el archivo de inicio si hace clic con el botón derecho en el archivo del proyecto y selecciona **Establecer como script R de inicio**. |
| | Reset R Interactive on Run (Restablecer R interactivo en ejecución) | Borra todas las variables del área de trabajo de la ventana interactiva al ejecutar el proyecto. Esto garantiza que no haya ningún contenido residual del área de trabajo de ejecuciones anteriores. |
| | Remote Project Path (Ruta de acceso remota del proyecto) | Ruta de acceso a un área de trabajo remota. |
| | Transfer files on run (Transferir archivos en ejecución) | Indica si los archivos del proyecto, sujetos al filtro en **Archivos que se transferirán**, deben copiarse en un área de trabajo remota con cada ejecución. |
| | Files to transfer (Archivos que se transferirán) | Nombres de archivo y caracteres comodín que indican los archivos específicos que se copiarán en un área de trabajo remota si **Transferencia de archivos en ejecución** está seleccionada. |
| Configuración | (Archivo Settings.R) | La configuración del proyecto de R procede de archivos *Settings.R* o **.Settings.R* que se encuentran dentro del proyecto. Si no hay ningún archivo de configuración, puede agregar variables, guardar la página y se creará un archivo *Settings.R* predeterminado. También puede agregar el archivo de configuración al proyecto mediante el comando de menú **Archivo** > **Agregar nuevo elemento**. <br/> La configuración se almacena como código de R y se puede especificar el origen del archivo antes de ejecutar otros módulos, rellenando previamente el entorno con la configuración predefinida. |

## <a name="r-specific-project-commands"></a>Comandos de proyecto específicos de R

Los proyectos de Visual Studio admiten un número de comandos generales mediante el menú contextual y el menú **Proyecto**. Para obtener más información sobre estas capacidades generales, vea [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Pero recuerde que Herramientas de R para Visual Studio (RTVS) agrega un número de comandos propios al menú contextual de un proyecto de R y también archivos y carpetas en el proyecto.

| Comando | Descripción |
| --- | --- |
| Establecer el directorio de trabajo aquí | Establece el directorio de trabajo de la ventana de R interactivo en la carpeta del proyecto, que también se puede usar en cualquier subcarpeta dentro de un proyecto. |
| Abrir carpeta Contenido | Abre el Explorador de Windows en la ubicación del archivo seleccionado. |
| Agregar script de R | Crea y abre un nuevo archivo *.R* con un nombre predeterminado. También puede usar el comando **Agregar** > **Nuevo elemento** para crear archivos *.R*, así como otros tipos de archivo. Vea [Plantillas de elementos específicas de R](#r-specific-item-templates). |
| Agregar Markdown de R | Crea y abre un documento *.rmd* con un nombre predeterminado. También puede usar el comando **Agregar** > **Nuevo elemento** para crear archivos *.rmd*, así como otros tipos de archivo. Vea [Plantillas de elementos específicas de R](#r-specific-item-templates).  |
| Publicar procedimientos almacenados | Inicia un proceso para publicar todos los procedimientos almacenados incluidos en scripts de R. Vea [Trabajar con procedimientos almacenados de SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Plantillas de elementos específicas de R

RTVS incluye una serie de plantillas para tipos de archivo específicos. Para acceder a las plantillas, haga clic con el botón derecho en un proyecto de R y seleccione **Agregar** > **Nuevo elemento**, seleccione **Proyecto** > **Agregar nuevo elemento** o vaya a **Archivo** > **Nuevo** > **Archivo** y seleccione la pestaña **R**. La mejor manera de explorar una plantilla es crear un proyecto e insertar los archivos de cada tipo.

> [!Note]
> Los comandos **Agregar** > **Nuevo elemento** muestran también los tipos de archivos generales que no se enumeran en la tabla; con **Archivo** > **Nuevo** > **Archivo**, esos tipos están contenidos en su lugar en la pestaña **General**.

| Tipo de archivo | Descripción |
| --- | --- |
| Script de R | Un archivo de texto que contiene los mismos comandos que se pueden escribir en la línea de comandos de R. |
| R Markdown | Un archivo que contiene un documento de [R Markdown](rmarkdown-with-r-in-visual-studio.md). |
| Configuración de R | Un archivo que contiene la configuración de la aplicación de R. |
| Documentación de R | Un archivo de documentación de R genérico que contiene solo el nombre, el alias y los campos de título. |
| Documentación de R (función) | Un archivo de documentación de R que contiene varios campos con comentarios para describir una función. |
| Documentación de R (conjunto de datos) | Un archivo de documentación de R que contiene varios campos con comentarios para describir un conjunto de datos. |
| Consulta SQL | Y un archivo *.sql* vacío. Vea [Trabajar con SQL Server y R](integrating-sql-server-with-r.md). |
| Procedimiento almacenado con R | Archivo de R con un archivo de plantilla de procedimientos almacenados secundarios y consultas SQL secundarias. Vea [Trabajar con SQL Server y R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Usar varios tipos de proyectos en Visual Studio

Soluciones de Visual Studio proporciona un lugar cómodo para recopilar y administrar proyectos relacionados en un lugar lógico. Las soluciones le ayudan a mantener el código organizado y facilitan la colaboración dentro de los equipos.

En el ejemplo siguiente, la solución contiene un proyecto de R con un modelo compilado mediante R y Azure Machine Learning, un proyecto de Python/scikit-learn, un proyecto de C++ que contiene módulos de trabajo de cálculo intensivo, un proyecto de SQL para la administración de datos y un proyecto de Python/Bottle para el sitio web que publica el resultado:

![Explorador de soluciones de Visual Studio con varios proyectos relacionados en una solución](media/projects-polyglot.png)

El proyecto resaltado en negrita es el proyecto de "inicio" de la solución; para cambiarlo, haga clic con el botón derecho en otro proyecto y seleccione **Establecer como proyecto de inicio**.

> [!Note]
> Actualmente, no hay ninguna integración de lenguaje explícita de R a C#/C++ (como hay para Python, vea [Creación de una extensión de C++ para Python](../python/working-with-c-cpp-python-in-visual-studio.md)).  En cambio, hay bibliotecas disponibles que proporcionan puentes de C# y C++ para R.

Para obtener más información sobre cómo administrar proyectos y soluciones en general, vea [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
