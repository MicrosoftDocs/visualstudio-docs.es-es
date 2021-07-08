---
title: Creación y uso de soluciones y proyectos de Visual Studio
description: Conozca la diferencia entre soluciones y proyectos y cómo usarlos en Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 713d320767bd329cc53b536bdad058a5db592b3f
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924934"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Creación, uso y eliminación de proyectos y soluciones de Visual Studio

En este artículo, aprenderá a crear y usar proyectos de Visual Studio desde cero para almacenar los artefactos que necesita para compilar las aplicaciones.  Si no está familiarizado con los proyectos de Visual Studio, vea esta introducción de [Proyectos y soluciones](solutions-and-projects-in-visual-studio.md).  Para obtener información sobre cómo crear rápidamente un proyecto a partir de una plantilla, vea [Creación de un proyecto a partir de una plantilla](create-new-project.md).

Los *proyectos* incluyen los elementos necesarios para compilar la aplicación, como archivos de código fuente, mapas de bits, iconos y referencias de componentes y servicios. Al crear un proyecto, Visual Studio crea una *solución* que lo contiene. Después, si quiere, puede agregar otros proyectos nuevos o existentes a la solución. Las soluciones también pueden contener archivos que no están conectados con ningún proyecto específico.

![Diagrama que muestra la jerarquía de la solución y del proyecto.](./media/vside-proj-soln.png)

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Crear proyectos en Visual Studio para Mac](/visualstudio/mac/create-new-projects).

Puede ver las soluciones y los proyectos en una ventana de herramientas denominada **Explorador de soluciones**. En la captura de pantalla siguiente se muestra una solución de ejemplo en el **Explorador de soluciones** (**BikeSharing.Xamarin-UWP**) que contiene dos proyectos: **BikeSharing.Clients.Core** y **BikeSharing.Clients.Windows**. Cada proyecto contiene varios archivos, carpetas y referencias. El nombre del proyecto en negrita es el *proyecto de inicio*, es decir, el proyecto que se inicia cuando se ejecuta la aplicación. Puede especificar qué proyecto es el de inicio.

![Captura de pantalla del Explorador de soluciones con dos proyectos.](./media/vside-solution-explorer-projects.png)

Aunque puede construir un proyecto por su cuenta si le agrega los archivos necesarios, Visual Studio ofrece diversas plantillas de proyecto como punto de partida. Si crea un proyecto a partir de una plantilla, dispondrá de un proyecto con los aspectos básicos de su tipo específico. Además, puede cambiar el nombre de los archivos o agregar código nuevo o existente y otros recursos según sea necesario.

Aun así, no hacen falta soluciones ni proyectos para desarrollar aplicaciones en Visual Studio. También puede abrir el código que haya clonado de Git o descargado de otro lugar. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Crear un proyecto a partir de una plantilla de proyecto

Para obtener información sobre cómo seleccionar una plantilla para crear un nuevo proyecto, vea [Creación de un proyecto en Visual Studio](create-new-project.md). Y para obtener un ejemplo de un proyecto y una solución creados desde cero con instrucciones paso a paso y código de ejemplo, vea [Información sobre proyectos y soluciones](../get-started/tutorial-projects-solutions.md).

## <a name="create-a-project-from-existing-code-files"></a>Crear un proyecto a partir de archivos de código existentes

Si tiene una colección de archivos de código fuente, puede agregarlos fácilmente a un proyecto.

1. En el menú, seleccione **Archivo** > **Nuevo** > **Proyecto a partir de código existente**.

1. En el **Asistente para crear proyectos a partir de archivos de código existentes**, seleccione el tipo de proyecto que quiera en el cuadro de lista desplegable **¿Qué tipo de proyecto desea crear?** y, después, haga clic en el botón **Siguiente**.

1. En el asistente, vaya a la ubicación de los archivos y escriba un nombre para el nuevo proyecto en el cuadro **Nombre**. Cuando haya terminado, seleccione el botón **Finalizar**.

> [!NOTE]
> Esta opción funciona mejor con una recopilación de archivos relativamente simple. Actualmente, solo se admiten los tipos de proyecto de C++, Apache Cordova, Visual Basic y C#.

## <a name="add-files-to-a-solution"></a>Agregar archivos a una solución

Si tiene un archivo que se aplica a varios proyectos, como un archivo Léame para la solución u otros archivos que pertenecen lógicamente al nivel de solución en lugar de a un proyecto específico, puede agregarlos a la propia solución. Para agregar un elemento a una solución, en el menú contextual (clic con el botón derecho) del nodo de la solución en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo elemento**, o bien **Agregar** > **Elemento existente**.

> [!TIP]
> Un archivo de solución es una estructura para organizar los proyectos en Visual Studio. Contiene el estado de esa información en dos archivos: un archivo *.sln* (basado en texto y compartido) y un archivo *.suo* (binario, oculto y de opciones de solución específicas del usuario). Por lo tanto, una solución no es algo que deba copiarse y cambiarse de nombre; es mejor crear una nueva solución y, después, agregarle elementos existentes.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Crear un proyecto .NET que tenga como destino una versión concreta de .NET Framework

Al crear un proyecto de .NET Framework, puede especificar una versión concreta de .NET Framework que quiera que use el proyecto. (Al crear un proyecto de .NET Core, no especifique ninguna versión de Framework).

::: moniker range="vs-2017"

Para especificar una versión de .NET Framework, seleccione el menú desplegable **Marco** en el cuadro de diálogo **Nuevo proyecto**.

![Captura de pantalla del menú desplegable Marco en el cuadro de diálogo Nuevo proyecto.](./media/vside-newproject-framework.png)

> [!NOTE]
> Para obtener acceso a versiones de .NET Framework anteriores a la 4, debe tener instalado .NET Framework 3.5 en el sistema.

::: moniker-end

::: moniker range=">=vs-2019"

Para especificar una versión de .NET Framework, seleccione el menú desplegable **Marco** en la página **Crear un proyecto**.

![Captura de pantalla del selector del menú Marco en el cuadro de diálogo "Configure su nuevo proyecto".](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Crear soluciones vacías

También puede crear soluciones vacías que no contengan ningún proyecto. Esto podría ser preferible si le interesa construir la solución y los proyectos desde cero.

### <a name="to-create-an-empty-solution"></a>Para crear una solución vacía

1. En la barra de menús, seleccione **Archivo**  > **Nuevo** > **Proyecto**.

::: moniker range="vs-2017"

2. En el panel izquierdo (**Plantillas**), seleccione **Otros tipos de proyectos** > **Soluciones de Visual Studio** en la lista expandida.

3. En el panel central, seleccione **Solución en blanco**.

4. Escriba los valores de **Nombre** y **Ubicación** para la solución y luego seleccione **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

2. En el cuadro de búsqueda de la página **Crear un proyecto**, escriba **solución**.

3. Seleccione la plantilla **Solución en blanco** y haga clic en **Siguiente**.

4. Escriba los valores de **Nombre** y **Ubicación** para la solución y luego seleccione **Crear**.

::: moniker-end

Después de crear una solución vacía, puede agregarle elementos o proyectos nuevos o existentes al seleccionar **Agregar nuevo elemento** o **Agregar elemento existente** en el menú **Proyecto**.

Como ya se ha indicado, también puede abrir archivos de código sin un proyecto o una solución. Para obtener información sobre el desarrollo de código de esta manera, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Creación de un proyecto temporal

(Solo C# y Visual Basic)

Si crea un proyecto basado en .NET sin especificar una ubicación de disco, el proyecto será temporal. Los proyectos temporales permiten experimentar con proyectos de .NET. Cuando trabaje con un proyecto temporal, podrá guardarlo o descartarlo en cualquier momento.

Para crear un proyecto temporal, vaya primero a **Herramientas** > **Opciones** > **Proyectos y soluciones** > **General** y desactive la casilla **Guardar nuevos proyectos al crearlos**. Después, abra el cuadro de diálogo **Nuevo proyecto**.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Eliminar una solución, un proyecto o un elemento

Puede usar el menú contextual para eliminar o quitar soluciones, proyectos o elementos de Visual Studio, pero solo se quitarán de la solución o del proyecto actual.

Para eliminar del sistema una solución u otro componente de forma permanente, use el **Explorador de archivos** de Windows para eliminar la carpeta que contiene los archivos de solución *.sln* y *.suo*. (Antes de eliminar una solución, es aconsejable que haga una copia de seguridad de los proyectos y archivos en caso de que los necesite de nuevo).

> [!NOTE]
> El archivo *.suo* es un archivo oculto que no aparece en la configuración predeterminada del Explorador de archivos. Para mostrar los archivos ocultos, en el menú **Vista** del Explorador de archivos, seleccione la casilla **Elementos ocultos**.

### <a name="permanently-delete-a-solution"></a>Eliminación permanente de una solución

Puede acceder al Explorador de archivos de Windows mediante el Explorador de soluciones de Visual Studio. Esta es la manera de hacerlo.

1. En el **Explorador de soluciones**, en el menú contextual (clic con el botón derecho) de la solución que quiera eliminar, seleccione **Abrir la carpeta en el Explorador de archivos**.

1. Suba un nivel en el Explorador de archivos.

1. Seleccione la carpeta que contiene la solución y presione la tecla **Suprimir**.

## <a name="see-also"></a>Consulte también

- [Introducción a proyectos y soluciones](../get-started/tutorial-projects-solutions.md)
- [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)
- [Soluciones filtradas en Visual Studio](filtered-solutions.md)
- [Repositorios de código abierto de Microsoft en GitHub](https://github.com/Microsoft)
- [Ejemplos de código para desarrolladores](https://code.msdn.microsoft.com/)
- [Recursos para solucionar problemas de errores en el entorno de desarrollo integrado](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
