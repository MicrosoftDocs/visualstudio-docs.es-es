---
title: Crear un proyecto nuevo
ms.date: 03/19/2019
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7cecf6a68296b3bffd07cca13fc3a3d0d5bc836
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770743"
---
# <a name="create-a-new-project-in-visual-studio"></a>Creación de un proyecto nuevo en Visual Studio

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Apertura del cuadro de diálogo Nuevo proyecto

Hay varias maneras de crear un proyecto en Visual Studio 2017. En la página Inicio, puede escribir el nombre de una plantilla de proyecto en el cuadro **Buscar plantillas de proyecto** o elegir el vínculo **Crear proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**. Aparte de la página Inicio, también puede elegir **Archivo** > **Nuevo** > **Proyecto** en la barra de menús, o bien hacer clic en el botón **Nuevo proyecto** de la barra de herramientas.

![Página de inicio con las opciones Archivo > Nuevo > Proyecto resaltadas](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selección de un tipo de plantilla

En el cuadro de diálogo **Nuevo proyecto**, aparecen las plantillas de proyecto disponibles en una lista en la categoría **Plantillas**. Las plantillas están organizadas por lenguaje de programación y tipo de proyecto, como Visual C#, JavaScript y Azure Data Lake.

![Cuadro de diálogo Nuevo proyecto](./media/vside-newproject-templates-list.png)

> [!NOTE]
> La lista de lenguajes y plantillas de proyecto disponibles que aparece depende de la versión de Visual Studio que se ejecute y de las cargas de trabajo que estén instaladas. Para obtener información sobre cómo instalar otras cargas de trabajo, vea [Modificación de Visual Studio mediante la incorporación o la eliminación de cargas de trabajo y componentes](../install/modify-visual-studio.md).

Muestre la lista de plantillas del lenguaje de programación que quiera usar. Para ello, haga clic en el triángulo situado junto al nombre de lenguaje y luego elija una categoría de proyecto (como Escritorio de Windows).

En la imagen siguiente se muestran las plantillas de proyecto disponibles para proyectos .NET Core de Visual C#:

![Plantillas de proyecto](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurar el proyecto

Escriba un nombre para el nuevo proyecto en el cuadro **Nombre**. Puede guardar el proyecto en la ubicación predeterminada en el sistema, o bien hacer clic en el botón **Examinar** para buscar otra ubicación. También puede elegir el nombre de una solución o agregar el nuevo proyecto en un repositorio de Git (para ello, elija **Agregar al control de código fuente**).

Haga clic en **Aceptar** para crear la solución y el proyecto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Apertura de la página Crear un proyecto

Hay varias maneras de crear un proyecto en Visual Studio 2019. Al abrir Visual Studio por primera vez, aparecerá la ventana de inicio y, desde allí, podrá elegir **Crear un proyecto**.

![Creación de un proyecto desde la ventana de inicio en VS 2019](media/vs-2019/start-window-create-new-project.png)

Si el entorno de desarrollo de Visual Studio ya está abierto, puede crear un proyecto eligiendo **Archivo** > **Nuevo** > **Proyecto** en la barra de menús o haciendo clic en el botón **Nuevo proyecto** de la barra de herramientas.

![Botón Nuevo proyecto de Visual Studio 2019](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Selección de un tipo de plantilla

A la izquierda de la página **Crear un proyecto**, aparece una lista de las plantillas seleccionadas recientemente. Las plantillas se ordenan por *usados más recientemente*.

Si no selecciona de las plantillas utilizadas recientemente, puede filtrar todas las plantillas de proyecto disponibles por **Lenguaje** (por ejemplo, C# o C++), **Plataforma** (por ejemplo, Windows o Azure) y **Tipo de proyecto** (por ejemplo, Escritorio o Web). También puede escribir el texto de búsqueda en el cuadro de búsqueda para filtrar aún más las plantillas, por ejemplo, **asp.net**.

![Filtros de plantilla de proyecto en Visual Studio 2019](media/vs-2019/create-new-project-filters.png)

Las etiquetas que aparecen debajo de cada plantilla se corresponden con los tres filtros de la lista desplegable (Lenguaje, Plataforma y Tipo de proyecto).

> [!TIP]
> Si no ve la plantilla que busca, puede que falte una carga de trabajo para Visual Studio. Si desea instalar cargas de trabajo adicionales, por ejemplo, de **Desarrollo de Azure** o **Desarrollo para dispositivos móviles con .NET**, haga clic en el vínculo **Instalar más herramientas y características** para abrir el instalador de Visual Studio. Desde allí, seleccione las cargas de trabajo que quiere instalar y luego elija **Modificar**. Después, las plantillas de proyecto adicionales estarán disponibles para su elección.
>
> ![Vínculo Instalar más herramientas y características en VS 2019](media/vs-2019/install-more-tools-features.png)

Seleccione una plantilla y haga clic en **Siguiente**.

## <a name="configure-your-project"></a>Configurar el proyecto

La página **Configurar el nuevo proyecto** incluye opciones para asignar nombre al proyecto (y la solución), elegir una ubicación de disco y seleccionar una versión de Framework (si se aplica a la plantilla elegida).

![Página Configurar el nuevo proyecto de VS 2019](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Si crea un proyecto cuando ya ha abierto un proyecto o una solución en Visual Studio, hay una opción de configuración adicional disponible. Puede crear una nueva solución o agregar el nuevo proyecto a la solución que ya está abierta.
>
> ![Creación de una solución o incorporación a una solución existente en VS 2019](media/vs-2019/configure-new-project-solution.png)

Haga clic en **Crear** para crear el proyecto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Incorporación de proyectos adicionales a una solución

Si quiere agregar un proyecto adicional a una solución, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y elija **Agregar** > **Nuevo proyecto**.

## <a name="see-also"></a>Vea también

- [Creación de soluciones y proyectos](creating-solutions-and-projects.md)
