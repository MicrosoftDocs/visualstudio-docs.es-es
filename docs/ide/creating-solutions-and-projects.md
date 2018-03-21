---
title: "Creación de soluciones y proyectos en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/06/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 23e91f8c5908efb4eed942a9c2556de7778fda92
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="create-solutions-and-projects"></a>Crear soluciones y proyectos

Los *proyectos* son contenedores lógicos de Visual Studio que incluyen los elementos necesarios para compilar la aplicación, como archivos de código fuente, mapas de bits, iconos y referencias de componentes y servicios. Al crear un proyecto, Visual Studio crea una *solución* que lo contiene. Después, si quiere, puede agregar otros proyectos nuevos o existentes a la solución. Las soluciones también pueden contener archivos que no están conectados con ningún proyecto específico.

![Jerarquía de soluciones y proyectos](./media/vside-proj-soln.png)

Puede ver las soluciones y los proyectos en una ventana de herramientas denominada **Explorador de soluciones**. En la captura de pantalla siguiente se muestra una solución de ejemplo en el Explorador de soluciones (BikeSharing.Xamarin-UWP) que contiene dos proyectos: BikeSharing.Clients.Core y BikeSharing.Clients.Windows. Cada proyecto contiene varios archivos, carpetas y referencias. El nombre del proyecto en negrita es el *proyecto de inicio*, es decir, el proyecto que se inicia cuando se ejecuta la aplicación. Puede especificar qué proyecto es el de inicio.

![Explorador de soluciones con proyectos](./media/vside-solution-explorer-projects.png)

Aunque puede construir un proyecto por su cuenta si le agrega los archivos necesarios, Visual Studio ofrece diversas plantillas de proyecto como punto de partida. Si crea un proyecto a partir de una plantilla, dispondrá de un proyecto con los aspectos básicos de su tipo específico. Además, puede cambiar el nombre de los archivos o agregar código nuevo o existente y otros recursos según sea necesario.

Aun así, no hacen falta soluciones ni proyectos para desarrollar aplicaciones en Visual Studio. También puede abrir el código que haya clonado de Git o descargado de otro lugar. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Las descripciones de este tema se basan en Visual Studio Community. Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los aquí descritos, en función de la configuración o la edición de Visual Studio. Para cambiar la configuración, por ejemplo, **General** o **Visual C++**, elija **Herramientas**, **Importar y exportar configuraciones** y, después, **Restablecer todas las configuraciones**.

## <a name="to-create-a-project-from-a-project-template"></a>Para crear un proyecto a partir de una plantilla de proyecto

1. Hay varias maneras de crear un proyecto en Visual Studio. En la página de inicio, escriba el nombre de una plantilla de proyecto en el cuadro **Buscar plantillas de proyecto** o elija el vínculo **Crear nuevo proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**. También puede seleccionar **Archivo** > **Nuevo** > **Proyecto…** en la barra de menús, o bien hacer clic en el botón **Nuevo proyecto** de la barra de herramientas.

  ![Página de inicio](./media/vside-newproject1.png)

  En el cuadro de diálogo **Nuevo proyecto**, aparecen las plantillas de proyecto disponibles en una lista en la categoría **Plantillas**. Las plantillas están organizadas por lenguaje de programación y tipo de proyecto, como Visual C#, JavaScript y Azure Data Lake.

  ![Cuadro de diálogo Nuevo proyecto](./media/vside-newproject-templates-list.png)

  > [!NOTE]
  > La lista de lenguajes y plantillas de proyecto disponibles que aparece depende de la versión de Visual Studio que se ejecute y de las cargas de trabajo que estén instaladas. Para obtener información sobre cómo instalar cargas de trabajo adicionales, vea [Modificación de Visual Studio 2017 mediante la incorporación o la eliminación de cargas de trabajo y componentes](../install/modify-visual-studio.md).

1. Muestre la lista de plantillas del lenguaje de programación que quiera usar. Para ello, seleccione el triángulo situado junto al nombre de lenguaje y, después, elija un tipo de proyecto.

  En el ejemplo siguiente se muestran las plantillas de proyecto disponibles para proyectos .NET Core de Visual C#.

  ![Plantillas de proyecto](./media/new-project-dialog-net-core.png)

1. Escriba un nombre para el nuevo proyecto en el cuadro **Nombre**. Puede guardar el proyecto en la ubicación predeterminada en el sistema, o bien seleccionar el botón **Examinar** para buscar otra ubicación.

  También puede cambiar el nombre de la solución o agregar el nuevo proyecto en un repositorio de Git. Para ello, elija **Agregar a control de código fuente**.

1. Elija el botón **Aceptar** para crear la solución y el proyecto.

1. Si quiere agregar un proyecto adicional a la solución, seleccione el nodo de la solución en el Explorador de soluciones y, después, en la barra de menús, elija **Proyecto** > **Agregar nuevo elemento**.

## <a name="create-a-project-from-existing-code-files"></a>Crear un proyecto a partir de archivos de código existentes

Si tiene una colección de archivos de código fuente, puede agregarlos fácilmente a un proyecto.

1. En el menú, elija **Archivo** > **Nuevo** > **Proyecto a partir de código existente**.

1. En el **Asistente para crear proyectos a partir de archivos de código existentes**, seleccione el tipo de proyecto que quiera en el cuadro de lista desplegable **¿Qué tipo de proyecto desea crear?** y, después, elija el botón **Siguiente** .

1. En el asistente, vaya a la ubicación de los archivos y escriba un nombre para el nuevo proyecto en el cuadro **Nombre**. Cuando haya terminado, elija el botón **Finalizar**.

> [!NOTE]
> Esta opción funciona mejor con una recopilación de archivos relativamente simple. Actualmente, solo se admiten los tipos de proyecto de Visual C++, Apache Cordova, Visual Basic y C#.

## <a name="add-files-to-a-solution"></a>Agregar archivos a una solución

Si tiene un archivo que se aplica a varios proyectos, como un archivo Léame para la solución u otros archivos que pertenecen lógicamente al nivel de solución en lugar de a un proyecto específico, puede agregarlos a la propia solución. Para agregar un elemento a una solución, en el menú contextual (clic con el botón derecho) del nodo de la solución en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo elemento**, o bien **Agregar** > **Elemento existente**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Crear un proyecto .NET que tenga como destino una versión concreta de .NET Framework

Cuando cree un proyecto, puede especificar la versión específica de .NET Framework que quiere que use el proyecto. Para especificar una versión de .NET Framework, seleccione el menú desplegable **Plataforma** en el cuadro de diálogo **Nuevo proyecto**.

![Desplegable Plataforma en el cuadro de diálogo Nuevo proyecto](./media/vside-newproject-framework.png)

> [!NOTE]
> Para obtener acceso a versiones de .NET Framework anteriores a la 4, debe tener instalado .NET Framework 3.5 en el sistema.

## <a name="create-empty-solutions"></a>Crear soluciones vacías

También puede crear soluciones vacías que no contengan ningún proyecto. Esto podría ser preferible si le interesa construir la solución y los proyectos desde cero.

### <a name="to-create-an-empty-solution"></a>Para crear una solución vacía

1. En el menú, elija **Archivo** > **Nuevo** > **Proyecto...**

1. En el panel izquierdo (**Plantillas**), seleccione **Otros tipos de proyectos** > **Soluciones de Visual Studio** en la lista expandida.

1. En el panel central, seleccione **Solución en blanco**.

1. Establezca los valores de **Nombre** y **Ubicación** de la solución y seleccione **Aceptar**.

Después de crear una solución vacía, puede agregarle elementos o proyectos nuevos o existentes al seleccionar **Agregar nuevo elemento** o **Agregar elemento existente** en el menú **Proyecto**.

Como ya se ha indicado, también puede abrir archivos de código sin un proyecto o una solución. Para obtener información sobre el desarrollo de código de esta manera, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Crear un proyecto temporal (C# y Visual Basic)

Si crea un proyecto basado en .NET sin especificar una ubicación de disco, el proyecto será temporal. Los proyectos temporales permiten experimentar con proyectos de .NET. Cuando trabaje con un proyecto temporal, podrá guardarlo o descartarlo en cualquier momento.

Para crear un proyecto temporal, vaya primero a **Herramientas** > **Opciones** > **Proyectos y soluciones** > **General** y desactive la casilla **Guardar nuevos proyectos al crearlos**. Después, abra el cuadro de diálogo **Nuevo proyecto**.

## <a name="delete-a-solution-project-or-item"></a>Eliminar una solución, un proyecto o un elemento

Puede eliminar las soluciones y su contenido de forma permanente, pero no mediante el IDE de Visual Studio. Cuando se eliminan elementos en Visual Studio, solo se eliminan de la solución o proyecto actual. Para eliminar del sistema una solución u otro componente de forma permanente, use el Explorador de archivos para eliminar la carpeta que contiene los archivos de solución .sln y .suo. No obstante, antes de eliminar permanentemente una solución, se recomienda que haga una copia de seguridad de todos los proyectos o archivos por si vuelve a necesitarlos.

> [!NOTE]
> El archivo .suo es un archivo oculto que no aparece en la configuración predeterminada del Explorador de archivos. Para mostrar los archivos ocultos, en el menú **Vista** del Explorador de archivos, seleccione la casilla **Elementos ocultos**.

### <a name="to-permanently-delete-a-solution"></a>Para eliminar permanentemente una solución

1. En el **Explorador de soluciones**, en el menú contextual de la solución que quiere eliminar, seleccione **Abrir carpeta en el Explorador de archivos**.

1. Suba un nivel en el Explorador de archivos.

1. Seleccione la carpeta que contiene la solución y presione la tecla **Suprimir**.

## <a name="see-also"></a>Vea también

[Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)  
[Repositorios de código abierto de Microsoft en GitHub](https://github.com/Microsoft)  
[Ejemplos de Visual Studio](../ide/visual-studio-samples.md)  
[Ejemplos de código para desarrolladores](https://code.msdn.microsoft.com/)
