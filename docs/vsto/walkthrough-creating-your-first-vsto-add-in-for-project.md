---
title: 'Tutorial: Creación del primer complemento de VSTO para Project'
description: Cree un complemento de nivel de aplicación para Microsoft Project. Esta característica está disponible para la propia aplicación, independientemente de los proyectos que estén abiertos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48d7baf9605947818ffd79eb7312c0dbefe581ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824268"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Tutorial: Creación del primer complemento de VSTO para Project
  En este tutorial se muestra cómo crear un complemento de VSTO para Microsoft Office Project. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los proyectos que estén abiertos. Para obtener más información, vea [Introducción al desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un proyecto de complemento de VSTO de Project.

- Escribir código que usa el modelo de objetos de Project para agregar una tarea a un nuevo proyecto.

- Compilar y ejecutar el proyecto para probarlo.

- Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] o [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto

### <a name="to-create-a-new-project-in-visual-studio"></a>Para crear un nuevo proyecto en Visual Studio

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.

3. En el panel de plantillas, expanda **Visual C#** o **Visual Basic** y luego expanda **Office/SharePoint**.

4. En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .

5. En la lista de plantillas de proyecto, seleccione **Complemento de Project 2010** o **Complemento de Project 2013**.

6. En el cuadro **Nombre** , escriba **FirstProjectAddIn**.

7. Haga clic en **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstProjectAddIn** y abre el archivo de código **ThisAddIn** en el editor.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Escribir código que agrega una nueva tarea a un proyecto
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código usa el modelo de objetos de Project para agregar una tarea a un proyecto. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:

- Una definición parcial de la clase `ThisAddIn` . Esta clase ofrece un punto de entrada para el código y acceso al modelo de objetos de Project. Para obtener más información, [vea Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). El resto de la `ThisAddIn` clase se define en un archivo de código oculto que no debe modificar.

- Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown` . Se llama a estos controladores de eventos cuando Project carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue. Para obtener más información, vea [Eventos en proyectos de Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-task-to-a-new-project"></a>Para agregar una tarea a un nuevo proyecto

1. En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn` . Este código define un controlador de eventos para el evento `NewProject` de la clase `Microsoft.Office.Interop.MSProject.Application`.

    Cuando el usuario crea un nuevo proyecto, este controlador de eventos agrega una tarea al proyecto.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet1":::

   Para modificar el proyecto, en este ejemplo de código se usan los objetos siguientes:

- El campo `Application` de la clase `ThisAddIn` . El campo `Application` devuelve un objeto `Microsoft.Office.Interop.MSProject.Application`, que representa la instancia actual de Project.

- Parámetro `pj` del controlador de eventos para el evento NewProject. El parámetro `pj` es un objeto `Microsoft.Office.Interop.MSProject.Project`, que representa el proyecto. Para obtener más información, vea [Soluciones de proyecto](../vsto/project-solutions.md).

1. Si está usando C#, agregue el siguiente código al controlador de eventos `ThisAddIn_Startup` . Este código conecta el controlador `Application_Newproject` de eventos con el evento NewProject.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet2":::

## <a name="test-the-project"></a>Prueba del proyecto
 Al compilar y ejecutar el proyecto, compruebe que la nueva tarea aparece en el nuevo proyecto resultante.

### <a name="to-test-the-project"></a>Para probar el proyecto

1. Presione **F5** para compilar y ejecutar el proyecto. Microsoft Project inicia y abre automáticamente un nuevo proyecto en blanco.

     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Project detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, vea Introducción [al proceso de compilación de soluciones de Office.](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100))

2. Compruebe que se ha agregado una nueva tarea al proyecto en blanco.

3. Compruebe que aparece el texto siguiente en el campo **Nombre de tarea** de la tarea.

     **Este texto se agregó mediante código.**

4. Cierre Microsoft Project.

## <a name="clean-up-the-project"></a>Limpieza del proyecto
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Microsoft Project en el equipo de desarrollo.

### <a name="to-clean-up-your-project"></a>Para limpiar el proyecto

1. En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.

## <a name="next-steps"></a>Pasos siguientes
 Ahora que ha creado un complemento básico de VSTO para Project, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:

- Tareas de programación generales que puede realizar en complementos de VSTO para Project: [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Uso del modelo de objetos de Project: [Soluciones de proyecto](../vsto/project-solutions.md).

- Compilación y depuración de complementos de VSTO para Project: [compilar soluciones de Office](../vsto/building-office-solutions.md).

- Implementación de complementos de VSTO para Project: [implemente una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Consulte también
- [Programación de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Soluciones de proyecto](../vsto/project-solutions.md)
- [Compilación de soluciones de Office](../vsto/building-office-solutions.md)
- [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)
- [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
