---
title: Agregar controles a documentos de Office en tiempo de ejecución
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01daa9a0446cc35090e6e47787b338cc74a9b1c8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944967"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Agregar controles a documentos de Office en tiempo de ejecución
  Puede agregar controles a un documento de Microsoft Office Word y libro de Microsoft Office Excel en tiempo de ejecución. También puede quitar en tiempo de ejecución. Los controles que agregue o quite en tiempo de ejecución se denominan *controles dinámicos*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 En este tema se describe lo siguiente:  

- [Administrar controles en tiempo de ejecución mediante el uso de colecciones de controles](#ControlsCollection).  

- [Agregar controles host a documentos](#HostControls).  

- [Agregar controles de formularios Windows Forms a documentos](#WindowsForms).  

  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Agregar controles a una superficie del documento en tiempo de ejecución? ](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Administrar controles en tiempo de ejecución mediante el uso de colecciones de controles  
 Para agregar, obtener o quitar controles en tiempo de ejecución, use métodos auxiliares de <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection> objetos.  

 La forma de acceder a estos objetos depende del tipo de proyecto que esté desarrollando:  

-   En un proyecto de nivel de documento para Excel, use la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> de las clases `Sheet1`, `Sheet2`y `Sheet3` . Para obtener más información sobre estas clases, vea [elemento host Worksheet](../vsto/worksheet-host-item.md).  

-   En un proyecto de nivel de documento para Word, use la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la clase `ThisDocument` . Para obtener más información acerca de esta clase, vea [elemento host Document](../vsto/document-host-item.md).  

-   En un proyecto de complemento VSTO para Excel o Word, use el `Controls` propiedad de un <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> que generan en tiempo de ejecución. Para obtener más información acerca de cómo generar estos objetos en tiempo de ejecución, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Agregar controles  
 Los tipos <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection> incluyen métodos del asistente que puede utilizar para agregar controles host y controles comunes de formularios Windows Forms a documentos y hojas de cálculo. Cada nombre de método tiene el formato `Add`*clase de control*, donde *clase de control* es el nombre de clase del control que quiere agregar. Por ejemplo, para agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> al documento, use el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .  

 En el ejemplo de código siguiente se agrega un elemento <xref:Microsoft.Office.Tools.Excel.NamedRange> a `Sheet1` un proyecto de nivel de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Controles de acceso y eliminación  
 Puede usar la propiedad `Controls` de un elemento <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> para recorrer en iteración todos los controles del documento, incluidos los controles que agregó en tiempo de diseño. Los controles que agregó en tiempo de diseño también se denominan *controles estáticos*.  

 Puede quitar controles dinámicos mediante una llamada a la `Delete` método del control o mediante una llamada a la `Remove` método de cada colección de controles. El siguiente ejemplo de código utiliza el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> para quitar un elemento <xref:Microsoft.Office.Tools.Excel.NamedRange> de `Sheet1` en un proyecto de nivel de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 No se puede quitar controles estáticos en tiempo de ejecución. Si intenta utilizar los métodos `Delete` o `Remove` para quitar un control estático, se producirá una <xref:Microsoft.Office.Tools.CannotRemoveControlException>.  

> [!NOTE]  
>  No quite controles mediante programación en el controlador de eventos `Shutdown` del documento. Los elementos de la interfaz de usuario del documento ya no estarán disponibles cuando se produzca el evento `Shutdown` . Si quiere quitar controles antes de que se cierre el documento, agregue el código al controlador de eventos de otro evento, como <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> o <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> para Word, o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> para Excel.  

##  <a name="HostControls"></a> Agregar controles host a documentos  
 Cuando agregue controles host a documentos mediante programación, debe proporcionar un nombre que identifique de forma única el control y debe especificar en qué parte del documento se debe agregar el control. Para obtener instrucciones específicas, consulte los temas siguientes:  

- [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

- [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

- [Cómo: Agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)  

- [Cómo: Contenido de agregar controles a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

- [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

  Para obtener más información acerca de los controles host, consulte [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  

  Si un documento se guarda y después se cierra, todos los controles host creados dinámicamente se desconectan de sus eventos y pierden su funcionalidad de enlace de datos. Puede agregar código a la solución para volver a crear los controles host cuando se vuelva a abrir el documento. Para obtener más información, consulte [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  No se ofrecen métodos del asistente para los siguientes controles host, debido a que estos controles no se pueden agregar mediante programación a documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> y <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Agregar controles de formularios Windows Forms a documentos  
 Cuando se agrega mediante programación un control de formularios Windows Forms a un documento, debe proporcionar la ubicación del control y un nombre que lo identifique de forma única. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] proporciona métodos del asistente para cada control. Estos métodos están sobrecargados para que pueda pasar un intervalo o coordenadas concretas para la ubicación del control.  

 Cuando un documento se guarda y se cierra, todos los controles de formularios Windows Forms creados dinámicamente se quitan del documento. Puede agregar código a la solución para volver a crear los controles cuando se vuelva a abrir el documento. Si crea controles dinámicos de Windows Forms mediante el uso de un complemento de VSTO, los contenedores de ActiveX para los controles se dejan en el documento. Para obtener más información, consulte [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Los controles de formularios Windows Forms no se puede agregar mediante programación a documentos protegidos. Si desprotege mediante programación un documento de Word o una hoja de cálculo de Excel para agregar un control, debe escribir código adicional para quitar el contenedor de ActiveX del control cuando se cierre el documento. El contenedor de ActiveX del control no se elimina automáticamente de los documentos protegidos.  

### <a name="add-custom-controls"></a>Agregar controles personalizados  
 Si quiere agregar un elemento <xref:System.Windows.Forms.Control> que no es compatible con los métodos del asistente disponibles, como un control de usuario personalizado, use los métodos siguientes:  

- En Excel, use uno de los métodos <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> de un objeto <xref:Microsoft.Office.Tools.Excel.ControlCollection> .  

- En Word, use uno de los métodos <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> de un objeto <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

  Para agregar el control, pase el elemento <xref:System.Windows.Forms.Control>, una ubicación para el control y un nombre que identifique de forma única el control al método `AddControl`. El método `AddControl` devuelve un objeto que define cómo interactúa el control con el documento o la hoja de cálculo. El `AddControl` método devuelve un <xref:Microsoft.Office.Tools.Excel.ControlSite> (para Excel) o un <xref:Microsoft.Office.Tools.Word.ControlSite> objeto (para Word).  

  En el ejemplo de código siguiente, se muestra cómo utilizar el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> para agregar dinámicamente un control de usuario personalizado a una hoja de cálculo en un proyecto de Excel de nivel de documento. En este ejemplo, el control de usuario se denomina `UserControl1`y el elemento <xref:Microsoft.Office.Interop.Excel.Range> se llama `range1`. Para usar este ejemplo, ejecútelo desde una clase `Sheet`*n* del proyecto.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Usar a miembros de controles personalizados  
 Después de utilizar uno de los métodos `AddControl` para agregar un control a una hoja de cálculo o a un documento, ahora dispone de dos objetos de control diferentes:  

- El objeto <xref:System.Windows.Forms.Control> que representa el control personalizado.  

- El objeto `ControlSite`, `OLEObject` o `OLEControl` que representa el control después de agregarlo a la hoja de cálculo o al documento.  

  Muchos métodos y propiedades se comparten entre estos controles. Es importante tener acceso a estos miembros a través del control adecuado:  

- Para acceder a miembros que pertenezcan solo al control personalizado, use <xref:System.Windows.Forms.Control>.  

- Para acceder a miembros compartidos por los controles, use el objeto `ControlSite`, `OLEObject` o `OLEControl`.  

  Si accede a un miembro compartido desde <xref:System.Windows.Forms.Control>, se podría producir un error sin advertencia ni notificación, o se pueden generar resultados no válidos. Utilice siempre métodos o propiedades del objeto `ControlSite`, `OLEObject` o `OLEControl`, a menos que el método o la propiedad necesarios no estén disponibles; solo en ese caso debe hacer referencia a <xref:System.Windows.Forms.Control>.  

  Por ejemplo, tanto las clases <xref:Microsoft.Office.Tools.Excel.ControlSite> y <xref:System.Windows.Forms.Control> tienen una propiedad `Top`. Para obtener o establecer la distancia entre la parte superior del control y la parte superior del documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> de <xref:Microsoft.Office.Tools.Excel.ControlSite>, no la propiedad <xref:System.Windows.Forms.Control.Top%2A> de <xref:System.Windows.Forms.Control>.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Cómo: Agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Controles de Windows Forms en información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
