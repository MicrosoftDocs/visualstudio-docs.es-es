---
title: "Tutorial: Crear el primer complemento de VSTO para Excel"
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
  - "complementos [desarrollo de Office en Visual Studio], crear su primer proyecto"
  - "Excel [desarrollo de Office en Visual Studio], crear su primer proyecto"
ms.assetid: a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Tutorial: Crear el primer complemento de VSTO para Excel
  Este tutorial introductorio muestra cómo crear un complemento de nivel de aplicación para Microsoft Office Excel. Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de los libros que se abran.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO para Excel.  
  
-   Escribir código que usa el modelo de objetos de Excel para agregar texto un libro cuando se guarda.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto completado para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Crear el proyecto  
  
#### Para crear un nuevo proyecto de complemento de VSTO en Visual Studio  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o  **Visual Basic** y luego expanda **Office\/SharePoint**.  
  
4.  En el nodo **Office\/SharePoint** expandido, seleccione el nodo **Complementos de Office**.  
  
5.  En la lista de plantillas de proyecto, seleccione **Complemento de Excel 2010** o **Complemento de Excel 2013**.  
  
6.  En el cuadro **Nombre**, escriba **FirstExcelAddIn**.  
  
7.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstExcelAddIn** y abre el archivo de código ThisAddIn en el editor.  
  
## Escribir código para agregar texto al libro guardado  
 A continuación, agregue código al archivo de código ThisAddIn. El nuevo código utiliza el modelo de objetos de Excel para insertar texto reutilizable en la primera fila de la hoja de cálculo activa. La hoja de cálculo activa es la hoja de cálculo que está abierta cuando el usuario guarda el libro. De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisAddIn`. Esta clase proporciona un punto de entrada para el código y proporciona acceso al modelo de objetos de Excel. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md). El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown`. Se llama a estos controladores de eventos cuando Excel carga y descarga el complemento de VSTO. Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento cuando se descargue. Para obtener más información, consulta [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
#### Para agregar una línea de texto al libro guardado  
  
1.  En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn`. El nuevo código define un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, que se desencadena cuando se guarda un libro.  
  
     Cuando el usuario guarda un libro, el controlador de eventos agrega el nuevo texto al principio de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Si está utilizando C\#, agregue el siguiente código necesario para el controlador de eventos `ThisAddIn_Startup`. Este código se utiliza para conectar el controlador de eventos `Application_WorkbookBeforeSave` con el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Para modificar el libro cuando se guarda, los ejemplos de código anteriores utilizan los siguientes objetos:  
  
-   El campo `Application` de la clase `ThisAddIn`. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.Excel.Application> que representa la instancia actual de Excel.  
  
-   El parámetro `Wb` del controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. El parámetro `Wb` es un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> que representa el libro guardado. Para obtener más información, consulta [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
## Probar el proyecto  
  
#### Para probar el proyecto  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que se incluye en la carpeta de salida de compilación del proyecto. Visual Studio crea también un conjunto de entradas del registro que permiten que Excel detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO. Para obtener más información, consulta [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
2.  En Excel, guarde el libro.  
  
3.  Compruebe que el texto siguiente se agrega al libro.  
  
     **Este texto se agregó mediante código.**  
  
4.  Cierre Excel.  
  
## Limpiar el proyecto  
 Cuando termine de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del registro y la configuración de seguridad del equipo de desarrollo. De lo contrario, el complemento de VSTO se ejecutará cada vez que abra Excel en el equipo de desarrollo.  
  
#### Para limpiar el proyecto completado en el equipo de desarrollo  
  
1.  En el menú **Crear** de Visual Studio, haga clic en **Limpiar solución**.  
  
## Pasos siguientes  
 Ahora que ha creado un complemento básico de VSTO para Excel, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:  
  
-   Tareas de programación generales que puede realizar en complementos de VSTO: [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Tareas de programación específicas de los complementos de VSTO de Excel: [Soluciones de Excel](../vsto/excel-solutions.md).  
  
-   Usar el modelo de objetos de Excel: [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
-   Personalizar la interfaz de usuario \(UI\) de Excel, por ejemplo, agregando una pestaña personalizada a la cinta de opciones o creando su propio panel de acciones: [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Compilar y depurar los complementos de VSTO para Excel: [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar complementos de VSTO para Excel: [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  