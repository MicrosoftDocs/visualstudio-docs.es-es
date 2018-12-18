---
title: Programar complementos VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 522a3cbac565e217f0b6525fb6288f5b79908a78
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674456"
---
# <a name="program-vsto-add-ins"></a>Programar complementos VSTO
  Cuando se amplía una aplicación de Microsoft Office mediante la creación de un complemento VSTO, el código se escribe directamente en la clase `ThisAddIn` de su proyecto. Puede usar esta clase para realizar tareas tales como tener acceso al modelo de objetos de la aplicación host de Microsoft Office, personalizar la interfaz de usuario (UI) de la aplicación y exponer objetos del complemento VSTO en otras soluciones de Office.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Algunos aspectos de la escritura de código en proyectos de complementos VSTO difieren de otros tipos de proyectos de Visual Studio. Muchas de estas diferencias se deben a la forma en que los modelos de objetos de Office se exponen al código administrado. Para obtener más información, consulte [escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
 Para obtener información general sobre los complementos VSTO y otros tipos de soluciones puede crear mediante el uso de las herramientas de desarrollo de Office en Visual Studio, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-thisaddin-class"></a>Utilice la clase ThisAddIn  
 Puede empezar a escribir el código del complemento VSTO en la clase `ThisAddIn` . Visual Studio genera automáticamente esta clase en el *ThisAddIn.vb* (en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) o *ThisAddIn.cs* archivo en el proyecto de complemento VSTO de código (en C#). El elemento [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea automáticamente una instancia de esta clase cuando la aplicación de Microsoft Office carga el complemento VSTO.  
  
 Hay dos controladores de eventos predeterminados en la clase `ThisAddIn` . Para ejecutar el código cuando se carga el complemento VSTO, agregue el código al controlador de eventos `ThisAddIn_Startup` . Para ejecutar el código justo antes de que se descargue el complemento VSTO, agregue el código al controlador de eventos `ThisAddIn_Shutdown` . Para obtener más información acerca de estos controladores de eventos, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  En Outlook, de forma predeterminada, no siempre se llama al controlador de eventos `ThisAddIn_Shutdown` cuando el complemento VSTO se descarga. Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-object-model-of-the-host-application"></a>Obtener acceso al modelo de objeto de la aplicación host  
 Para obtener acceso al modelo de objetos de la aplicación host, utilice el campo `Application` de la clase `ThisAddIn` . Este campo devuelve un objeto que representa la instancia actual de la aplicación host. La siguiente tabla muestra el tipo de valor devuelto del campo `Application` en cada proyecto de complemento VSTO.  
  
|Aplicación host|Tipo de valor devuelto|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 En el ejemplo de código siguiente se muestra cómo utilizar el `Application` campo para crear un nuevo libro en un complemento VSTO para Microsoft Office Excel. Este ejemplo está pensado para ejecutarse desde la clase `ThisAddIn` .  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Para hacer lo mismo desde fuera de la clase `ThisAddIn` , use el objeto `Globals` para tener acceso a la clase `ThisAddIn` . Para obtener más información sobre la `Globals` de objetos, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:  
  
-   [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluciones de InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluciones de proyecto](../vsto/project-solutions.md)  
  
-   [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Obtener acceso a un documento cuando se inicia la aplicación de Office  
 No todas las aplicaciones [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] abren automáticamente un documento al iniciarlas, y ninguna de las aplicaciones [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] abre un documento al iniciarla. Por lo tanto, no agregue el código en el `ThisAdd-In_Startup` controlador de eventos si el código requiere que un documento esté abierto. En su lugar, agregue ese código a un evento que sea generado por la aplicación de Office cuando un usuario cree o abra un documento. De este modo, puede garantizar que haya un documento abierto para que el código realice operaciones en él.  
  
 El siguiente ejemplo de código funciona con un documento de Word sólo cuando el usuario crea un documento o abre un documento existente.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Miembros de ThisAddIn que se usará para otras tareas  
 La tabla siguiente se describen otras tareas habituales y muestra los miembros de la clase `ThisAddIn` que puede utilizar para realizar las tareas.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Ejecute el código para inicializar el complemento VSTO cuando este se cargue.|Agregue código al método `ThisAddIn_Startup` . Este es el controlador de eventos predeterminado para el evento <xref:Microsoft.Office.Tools.AddInBase.Startup> . Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).|  
|Ejecute el código para limpiar los recursos usados por el complemento VSTO antes de que este se descargue.|Agregue código al método `ThisAddIn_Shutdown` . Este es el controlador de eventos predeterminado para el evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md). **Nota:** en Outlook, de forma predeterminada el `ThisAddIn_Startup` controlador de eventos no siempre se llama cuando el complemento de VSTO se descarga. Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).|  
|Mostrar un panel de tareas personalizado.|Utilice el campo `CustomTaskPanes` . Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).|  
|Exponer objetos de un complemento VSTO en otras soluciones de Microsoft Office.|Invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Para obtener más información, consulte [llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Personalizar una característica del sistema Microsoft Office implementando una interfaz de extensibilidad.|Invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para que devuelva una instancia de una clase que implemente la interfaz. Para obtener más información, consulte [características de personalización de la interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Nota:** para personalizar la interfaz de usuario de la cinta de opciones, también puede invalidar el <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> método.|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>Entender el diseño de la clase ThisAddIn  
 En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> es una interfaz. La clase `ThisAddIn` se deriva de la clase <xref:Microsoft.Office.Tools.AddInBase> . Esta clase base redirige todas las llamadas a sus miembros a una implementación interna de la interfaz <xref:Microsoft.Office.Tools.AddIn> en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 En los proyectos de complemento VSTO para Outlook, la `ThisAddIn` clase se deriva de la `Microsoft.Office.Tools.Outlook.OutlookAddIn` clase en proyectos que tienen como destino .NET Framework 3.5 y de <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> en los proyectos que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Estas clases base proporcionan funciones adicionales para admitir las áreas de formulario. Para obtener más información acerca de las áreas de formulario, consulte [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personalizar la interfaz de usuario de aplicaciones de Microsoft Office  
 Puede personalizar mediante programación la interfaz de usuario de las aplicaciones de Microsoft Office mediante un complemento VSTO. Por ejemplo, puede personalizar la cinta de opciones, mostrar un panel de tareas personalizado o crear un área de formulario personalizada en Outlook. Para obtener más información, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 Visual Studio proporciona diseñadores y clases que puede utilizar para crear paneles de tareas personalizados, personalizaciones de la cinta de opciones y áreas de formulario de Outlook. Estos diseñadores y clases ayudan a simplificar el proceso de personalización de estas características. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md), [Ribbon Designer](../vsto/ribbon-designer.md), y [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).  
  
 Si desea personalizar una de estas características de forma que no sea compatible con las clases y los diseñadores, puede personalizarlas mediante la implementación de una *interfaz de extensibilidad* en el complemento VSTO. Para obtener más información, consulte [características de personalización de la interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Además, puede modificar la interfaz de usuario de los documentos de Word y libros de Excel generando elementos host que extienden el comportamiento de documentos y libros. Esto le permite agregar controles administrados a documentos y hojas de cálculo. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Llamar a código en complementos VSTO desde otras soluciones  
 Puede exponer los objetos de su complemento VSTO en otras soluciones (incluidas otras soluciones de Microsoft Office). Esto resulta útil si su complemento VSTO proporciona un servicio que quiera habilitar para que lo usen otras soluciones. Por ejemplo, si tiene un complemento VSTO para Microsoft Office Excel que realiza cálculos sobre datos financieros desde un servicio web, otras soluciones pueden realizar estos cálculos llamando al complemento VSTO de Excel en tiempo de ejecución.  
  
 Para obtener más información, consulte [llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Tutorial: Llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Personalizar las características de interfaz de usuario mediante interfaces de extensibilidad](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  