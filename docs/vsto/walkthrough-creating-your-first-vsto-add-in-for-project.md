---
title: "Tutorial: Crear el primer complemento de VSTO para Project | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], crear su primer proyecto"
  - "desarrollo de Office en Visual Studio, crear su primer proyecto"
  - "Project [desarrollo de Office en Visual Studio], crear su primer proyecto"
  - "complementos [desarrollo de Office en Visual Studio], crear su primer proyecto"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Tutorial: Crear el primer complemento de VSTO para Project
  Este tutorial muestra cómo crear un complemento de VSTO para Microsoft Office Project. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los proyectos que estén abiertos. Para obtener más información, consulta [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO de Project.  
  
-   Escribir código que usa el modelo de objetos de Project para agregar una tarea a un nuevo proyecto.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] o [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## Crear el proyecto  
  
#### Para crear un nuevo proyecto en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o  **Visual Basic** y luego expanda **Office\/SharePoint**.  
  
4.  En el nodo **Office\/SharePoint** expandido, seleccione el nodo **Complementos de Office**.  
  
5.  En la lista de plantillas de proyecto, seleccione **Complemento de Project 2010** o **Complemento de Project 2013**.  
  
6.  En el cuadro **Nombre**, escriba **FirstProjectAddIn**.  
  
7.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstProjectAddIn** y abre el archivo de código **ThisAddIn** en el editor.  
  
## Escribir código que agrega una nueva tarea a un proyecto  
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código usa el modelo de objetos de Project para agregar una tarea a un proyecto. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisAddIn`. Esta clase ofrece un punto de entrada para el código y acceso al modelo de objetos de Project. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md). El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown`. Se llama a estos controladores de eventos cuando Project carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue. Para obtener más información, consulta [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
#### Para agregar una tarea a un nuevo proyecto  
  
1.  En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn`. Este código define un controlador de eventos para el evento NewProject de la clase Microsoft.Office.Interop.MSProject.Application.  
  
     Cuando el usuario crea un nuevo proyecto, este controlador de eventos agrega una tarea al proyecto.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 Para modificar el proyecto, este ejemplo de código usa los siguientes objetos:  
  
-   El campo `Application` de la clase `ThisAddIn`. El campo `Application` devuelve un objeto Microsoft.Office.Interop.MSProject.Application, que representa la instancia actual de Project.  
  
-   El parámetro `pj` del controlador de eventos para el evento NewProject. El parámetro `pj` es un objeto Microsoft.Office.Interop.MSProject.Project, que representa el proyecto. Para obtener más información, consulta [Soluciones de Project](../vsto/project-solutions.md).  
  
1.  Si está usando C\#, agregue el siguiente código al controlador de eventos `ThisAddIn_Startup`. Este código conecta el controlador de eventos `Application_Newproject` con el evento NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## Probar el proyecto  
 Al compilar y ejecutar el proyecto, compruebe que la nueva tarea aparece en el nuevo proyecto resultante.  
  
#### Para probar el proyecto  
  
1.  Presione **F5** para compilar y ejecutar el proyecto. Microsoft Project inicia y abre automáticamente un nuevo proyecto en blanco.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Project detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, vea [Información general acerca del proceso de compilación de soluciones de Office](http://msdn.microsoft.com/es-es/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Compruebe que se ha agregado una nueva tarea al proyecto en blanco.  
  
3.  Compruebe que aparece el texto siguiente en el campo **Nombre de tarea** de la tarea.  
  
     **Este texto se agregó mediante código.**  
  
4.  Cierre Microsoft Project.  
  
## Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Microsoft Project en el equipo de desarrollo.  
  
#### Para limpiar el proyecto  
  
1.  En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.  
  
## Pasos siguientes  
 Ahora que ha creado un complemento básico de VSTO para Project, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:  
  
-   Tareas de programación generales que puede realizar en complementos de VSTO para Project: [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Usar el modelo de objetos de Project: [Soluciones de Project](../vsto/project-solutions.md).  
  
-   Compilar y depurar los complementos de VSTO para Project: [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar complementos de VSTO para Project: [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluciones de Project](../vsto/project-solutions.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  