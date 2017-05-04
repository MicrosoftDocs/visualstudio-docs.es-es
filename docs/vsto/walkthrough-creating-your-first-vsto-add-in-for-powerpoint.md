---
title: "Tutorial: Crear el primer complemento de VSTO para PowerPoint | Microsoft Docs"
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
  - "complementos [desarrollo de Office en Visual Studio], crear el primer proyecto"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], crear el primer proyecto"
  - "desarrollo de Office en Visual Studio, crear el primer proyecto"
  - "PowerPoint [desarrollo de Office en Visual Studio], crear el primer proyecto"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Tutorial: Crear el primer complemento de VSTO para PowerPoint
  Este tutorial muestra cómo crear un complemento de VSTO para Microsoft Office PowerPoint.  Las características que cree en este tipo de solución estarán disponibles para la propia aplicación, con independencia de qué presentaciones están abiertas.  Para obtener más información, vea [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto de complemento de VSTO de PowerPoint para PowerPoint.  
  
-   Escribir código que usa el modelo de objetos de PowerPoint para agregar un cuadro de texto a cada nueva diapositiva.  
  
-   Compilar y ejecutar el proyecto para probarlo.  
  
-   Limpiar el proyecto para que el complemento de VSTO deje de ejecutarse automáticamente en el equipo de desarrollo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## Crear el proyecto  
  
#### Para crear un nuevo proyecto  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o  **Visual Basic** y luego expanda **Office\/SharePoint**.  
  
4.  En el nodo **Office\/SharePoint** expandido, seleccione el nodo **Complementos de Office**.  
  
5.  En la lista de plantillas de proyecto, seleccione un proyecto de complemento de VSTO de PowerPoint.  
  
6.  En el cuadro **Nombre**, escriba **FirstPowerPointAddIn**.  
  
7.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea el proyecto **FirstPowerPointAddIn** y abre el archivo de código **ThisAddIn** en el editor.  
  
## Escribir código que agregue texto a cada nueva diapositiva  
 A continuación, agregue código al archivo de código ThisAddIn.  El nuevo código usa el modelo de objetos de PowerPoint para agregar un cuadro de texto a cada nueva diapositiva.  De forma predeterminada, el archivo de código ThisAddIn contiene el siguiente código generado:  
  
-   Una definición parcial de la clase `ThisAddIn`.  Esta clase proporciona un punto de entrada para el código y proporciona acceso al modelo de objetos de PowerPoint.  Para obtener más información, vea [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  El resto de la clase `ThisAddIn` se define en un archivo de código oculto que no se debe modificar.  
  
-   Los controladores de eventos `ThisAddIn_Startup` y `ThisAddIn_Shutdown`.  Se llama a estos controladores de eventos cuando PowerPoint carga y descarga el complemento de VSTO.  Use estos controladores de eventos para inicializar el complemento de VSTO cuando se cargue y para limpiar los recursos que usa el complemento de VSTO cuando se descargue.  Para obtener más información, vea [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
#### Para agregar un cuadro de texto a cada nueva diapositiva  
  
1.  En el archivo de código ThisAddIn, agregue el código siguiente a la clase `ThisAddIn`.  Este código define un controlador de eventos para el evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> del objeto <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Cuando el usuario agrega una nueva diapositiva a la presentación activa, este controlador de eventos agrega un cuadro de texto a la parte superior de la nueva diapositiva y agrega texto al cuadro de texto.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Si está usando C\#, agregue el siguiente código al controlador de eventos `ThisAddIn_Startup`.  Este código es necesario para conectar el controlador de eventos `Application_PresentationNewSlide` con el evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Para modificar cada nueva diapositiva, los ejemplos de código anteriores usan los siguientes objetos:  
  
-   El campo `Application` de la clase `ThisAddIn`.  El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.PowerPoint.Application> que representa la instancia actual de PowerPoint.  
  
-   El parámetro `Sld` del controlador de eventos para el evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  El parámetro `Sld` es un objeto <xref:Microsoft.Office.Interop.PowerPoint.Slide> que representa la nueva diapositiva.  Para obtener más información, vea [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md).  
  
## Probar el proyecto  
 Al compilar y ejecutar el proyecto, compruebe que aparece el cuadro de texto en las diapositivas nuevas que agregue a una presentación.  
  
#### Para probar el proyecto  
  
1.  Presione **F5** para compilar y ejecutar el proyecto.  
  
     Al compilar el proyecto, el código se compila en un ensamblado que se coloca en la carpeta de salida de compilación del proyecto.  Visual Studio crea también un conjunto de entradas del Registro que permiten que PowerPoint detecte y cargue el complemento de VSTO, y establece la configuración de seguridad en el equipo de desarrollo para permitir la ejecución del complemento de VSTO.  Para obtener más información, vea [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
2.  En PowerPoint, agregue una nueva diapositiva a la presentación activa.  
  
3.  Compruebe que el siguiente texto se agrega a un nuevo cuadro de texto en la parte superior de la diapositiva.  
  
     **Este texto se agregó mediante código.**  
  
4.  Cierre PowerPoint.  
  
## Limpiar el proyecto  
 Cuando haya terminado de desarrollar un proyecto, quite el ensamblado del complemento de VSTO, las entradas del Registro y la configuración de seguridad del equipo de desarrollo.  De lo contrario, el complemento de VSTO se ejecutará cada vez que abra PowerPoint en el equipo de desarrollo.  
  
#### Para limpiar el proyecto  
  
1.  En el menú **Compilar** de Visual Studio, haga clic en **Limpiar solución**.  
  
## Pasos siguientes  
 Ahora que ha creado un complemento básico de VSTO para PowerPoint, puede obtener más información sobre cómo desarrollar complementos de VSTO en estos temas:  
  
-   Tareas de programación generales que puede realizar en complementos de VSTO para PowerPoint.  Para obtener más información, vea [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Usar el modelo de objetos de PowerPoint.  Para obtener más información, vea [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personalizar la interfaz de usuario \(UI\) de PowerPoint, por ejemplo, agregando una pestaña personalizada a la cinta o creando su propio panel de tareas personalizado.  Para obtener más información, vea [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
-   Compilar y depurar los complementos de VSTO para PowerPoint.  Para obtener más información, consulte [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
-   Implementar complementos de VSTO para PowerPoint.  Para obtener más información, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)  
  
  