---
title: 'Tutorial: Crear el primer complemento VSTO para proyecto | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e1b768a8d812d3a4c0222bbb3e762c0f5046f56
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>Tutorial: Crear el primer complemento de VSTO para Project
  Este tutorial muestra cómo crear un complemento de VSTO para Microsoft Office Project. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los proyectos que estén abiertos. Para obtener más información, vea [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO de Project.  
  
-   Escribir código que usa el modelo de objetos de Project para agregar una tarea a un nuevo proyecto.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] o [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Crear el proyecto  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>Para crear un nuevo proyecto en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C#** o **Visual Basic**y luego expanda **Office/SharePoint**.  
  
4.  En el nodo **Office/SharePoint** expandido, seleccione el nodo **Complementos de Office** .  
  
5.  En la lista de plantillas de proyecto, seleccione **Complemento de Project 2010** o **Complemento de Project 2013**.  
  
6.  En el cuadro **Nombre** , escriba **FirstProjectAddIn**.  
  
7.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstProjectAddIn** y abre el archivo de código **ThisAddIn** en el editor.  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>Escribir código que agrega una nueva tarea a un proyecto  
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código usa el modelo de objetos de Project para agregar una tarea a un proyecto. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisAddIn` . Esta clase ofrece un punto de entrada para el código y acceso al modelo de objetos de Project. Para obtener más información, consulta [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown` . Se llama a estos controladores de eventos cuando Project carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue. Para obtener más información, consulta [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-task-to-a-new-project"></a>Para agregar una tarea a un nuevo proyecto  
  
1.  En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn` . Este código define un controlador de eventos para el evento nuevo proyecto de la clase Microsoft.Office.Interop.MSProject.Application.  
  
     Cuando el usuario crea un nuevo proyecto, este controlador de eventos agrega una tarea al proyecto.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 Para modificar el proyecto, este ejemplo de código usa los siguientes objetos:  
  
-   El campo `Application` de la clase `ThisAddIn` . El `Application` campo devuelve un objeto Microsoft.Office.Interop.MSProject.Application, que representa la instancia actual de Project.  
  
-   El `pj` parámetro del controlador de eventos para el evento nuevo proyecto. El `pj` parámetro es un objeto Microsoft.Office.Interop.MSProject.Project, que representa el proyecto. Para obtener más información, consulta [Project Solutions](../vsto/project-solutions.md).  
  
1.  Si está usando C#, agregue el siguiente código al controlador de eventos `ThisAddIn_Startup` . Este código conecta el `Application_Newproject` controlador de eventos con el evento nuevo proyecto.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>Probar el proyecto  
 Al compilar y ejecutar el proyecto, compruebe que la nueva tarea aparece en el nuevo proyecto resultante.  
  
#### <a name="to-test-the-project"></a>Para probar el proyecto  
  
1.  Presione **F5** para compilar y ejecutar el proyecto. Microsoft Project inicia y abre automáticamente un nuevo proyecto en blanco.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Project detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, vea [Información general acerca del proceso de compilación de soluciones de Office](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Compruebe que se ha agregado una nueva tarea al proyecto en blanco.  
  
3.  Compruebe que aparece el texto siguiente en el campo **Nombre de tarea** de la tarea.  
  
     **Este texto se agregó mediante código.**  
  
4.  Cierre Microsoft Project.  
  
## <a name="cleaning-up-the-project"></a>Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Microsoft Project en el equipo de desarrollo.  
  
#### <a name="to-clean-up-your-project"></a>Para limpiar el proyecto  
  
1.  En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora que ha creado un complemento básico de VSTO para Project, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:  
  
-   Tareas de programación generales que puede realizar en complementos de VSTO para Project: [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Usar el modelo de objetos de Project: [Project Solutions](../vsto/project-solutions.md).  
  
-   Compilar y depurar los complementos VSTO para Project: [compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar complementos VSTO para Project: [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Soluciones de Project](../vsto/project-solutions.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)  
  
  