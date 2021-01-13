---
title: Crear un proyecto nuevo
description: Aprenda a crear un nuevo proyecto en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
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
ms.openlocfilehash: dcbf39be441ba8237520fcc56ceec7946d688901
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846906"
---
# <a name="create-a-new-project-in-visual-studio"></a>Creación de un proyecto en Visual Studio

En este artículo, se mostrará cómo crear rápidamente un nuevo proyecto en Visual Studio.

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Apertura del cuadro de diálogo Nuevo proyecto

Hay varias maneras de crear un proyecto en Visual Studio 2017. En la página Inicio, puede escribir el nombre de una plantilla de proyecto en el cuadro **Buscar plantillas de proyecto** o seleccionar el vínculo **Crear proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**. Aparte de la página Inicio, también puede seleccionar **Archivo** > **Nuevo** > **Proyecto** en la barra de menús, o bien hacer clic en el botón **Nuevo proyecto** de la barra de herramientas.

![Captura de pantalla de la barra de menús de Visual Studio con las opciones Archivo > Nuevo > Proyecto seleccionadas.](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Selección de un tipo de plantilla

En el cuadro de diálogo **Nuevo proyecto**, aparecen las plantillas de proyecto disponibles en una lista en la categoría **Plantillas**. Las plantillas están organizadas por lenguaje de programación y tipo de proyecto, como Visual C#, JavaScript y Azure Data Lake.

![Captura de pantalla del cuadro de diálogo Nuevo proyecto en el que se muestra una lista de plantillas instaladas.](./media/vside-newproject-templates-list.png)

> [!NOTE]
> La lista de lenguajes y plantillas de proyecto disponibles que aparece depende de la versión de Visual Studio que se ejecute y de las cargas de trabajo que estén instaladas. Para obtener información sobre cómo instalar otras cargas de trabajo, vea [Modificación de Visual Studio mediante la incorporación o la eliminación de cargas de trabajo y componentes](../install/modify-visual-studio.md).

Muestre la lista de plantillas del lenguaje de programación que quiera usar. Para ello, haga clic en el triángulo situado junto al nombre de lenguaje y luego elija una categoría de proyecto (como Escritorio de Windows).

En la imagen siguiente se muestran las plantillas de proyecto disponibles para proyectos .NET Core de Visual C#:

![Captura de pantalla del cuadro de diálogo Nuevo proyecto en el que se muestran las plantillas de proyecto que puede elegir.](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Configurar el proyecto

Escriba un nombre para el nuevo proyecto en el cuadro **Nombre**. Puede guardar el proyecto en la ubicación predeterminada en el sistema, o bien hacer clic en el botón **Examinar** para buscar otra ubicación. También puede seleccionar el nombre de una solución o agregar el nuevo proyecto a un repositorio de Git (para ello, seleccione **Agregar a control de código fuente**).

Haga clic en **Aceptar** para crear la solución y el proyecto.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Apertura de la página Crear un proyecto

Hay varias maneras de crear un proyecto en Visual Studio 2019. Al abrir Visual Studio por primera vez, aparecerá la ventana de inicio y, desde allí, podrá seleccionar **Crear un proyecto**.

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="Captura de pantalla del cuadro de diálogo &quot;Crear un nuevo proyecto&quot; en la ventana de inicio de Visual Studio 2019.":::

Si el entorno de desarrollo de Visual Studio ya está abierto, puede crear un proyecto eligiendo **Archivo** > **Nuevo** > **Proyecto** en la barra de menús. También puede hacer clic en el botón **Nuevo proyecto** de la barra de herramientas, o bien presionar **Ctrl**+**Mayús**+**N**.

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Captura de pantalla del botón Nuevo proyecto de Visual Studio 2019.":::

## <a name="select-a-template-type"></a>Selección de un tipo de plantilla

A la izquierda de la página **Crear un proyecto**, aparece una lista de las plantillas seleccionadas recientemente. Las plantillas se ordenan por *usados más recientemente*.

Si no selecciona de las plantillas utilizadas recientemente, puede filtrar todas las plantillas de proyecto disponibles por **Lenguaje** (por ejemplo, C# o C++), **Plataforma** (por ejemplo, Windows o Azure) y **Tipo de proyecto** (por ejemplo, Escritorio o Web). También puede escribir el texto de búsqueda en el cuadro de búsqueda para filtrar aún más las plantillas, por ejemplo, **asp.net**.

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Captura de pantalla de los filtros de la plantilla de proyecto en Visual Studio 2019.":::

Las etiquetas que aparecen debajo de cada plantilla se corresponden con los tres filtros de la lista desplegable (Lenguaje, Plataforma y Tipo de proyecto).

> [!TIP]
> Si no ve la plantilla que busca, es posible que falte una carga de trabajo para Visual Studio. Si desea instalar cargas de trabajo adicionales, por ejemplo, de **Desarrollo de Azure** o **Desarrollo para dispositivos móviles con .NET**, haga clic en el vínculo **Instalar más herramientas y características** para abrir el instalador de Visual Studio. Desde allí, seleccione las cargas de trabajo que quiere instalar y luego seleccione **Modificar**. Después, las plantillas de proyecto adicionales estarán disponibles para su elección.
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Captura de pantalla del vínculo &quot;Instalar más herramientas y características&quot; en Visual Studio 2019.":::

Seleccione una plantilla y haga clic en **Siguiente**.

## <a name="configure-your-project"></a>Configurar el proyecto

La página **Configure su nuevo proyecto** incluye opciones para asignar un nombre al proyecto (y a la solución), elegir una ubicación de disco y seleccionar una versión de Framework (si se aplica a la plantilla elegida).

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Captura de pantalla de la página &quot;Configure su nuevo proyecto&quot; en Visual Studio 2019.":::

> [!NOTE]
> Si crea un proyecto cuando ya ha abierto un proyecto o una solución en Visual Studio, hay una opción de configuración adicional disponible. Puede crear una nueva solución o agregar el nuevo proyecto a la solución que ya está abierta.
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Captura de pantalla del cuadro de diálogo &quot;Crear nueva solución&quot; o &quot;Agregar a la solución&quot; en Visual Studio 2019.":::

Haga clic en **Crear** para crear el proyecto.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Incorporación de proyectos adicionales a una solución

Si quiere agregar un proyecto adicional a una solución, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

> [!TIP]
> Para obtener un ejemplo de un proyecto y una solución creados desde cero con instrucciones paso a paso y código de ejemplo, vea [Información sobre proyectos y soluciones](../get-started/tutorial-projects-solutions.md).

## <a name="see-also"></a>Consulte también

- [Introducción a proyectos y soluciones](../get-started/tutorial-projects-solutions.md)
- [Trabajar con soluciones y proyectos](creating-solutions-and-projects.md)
- [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)
- [Crear proyectos (Visual Studio para Mac)](/visualstudio/mac/create-new-projects)