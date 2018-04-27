---
title: Agregar controles a documentos de Office en tiempo de ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f36e98d79f8037aba2a2f1a50d9a7fb3915a94c
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="adding-controls-to-office-documents-at-run-time"></a>Agregar controles a documentos de Office en tiempo de ejecución
  Puede agregar controles a un documento de Microsoft Office Word y a un libro de Microsoft Office Excel en tiempo de ejecución. También puede quitarlos en tiempo de ejecución. Los controles que agregue o quite en tiempo de ejecución se denominan *controles dinámicos*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 En este tema se describe lo siguiente:  

-   [Administrar controles en tiempo de ejecución mediante las colecciones de controles](#ControlsCollection).  

-   [Agregar controles host a documentos](#HostControls).  

-   [Agregar controles de formularios Windows Forms a documentos](#WindowsForms).  

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [Cómo: agregar controles a una superficie del documento en tiempo de ejecución?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Managing Controls at Run Time by Using the Control Collections  
 Para agregar, obtener o quitar controles en tiempo de ejecución, use los métodos auxiliares de los objetos <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

 La forma de acceder a estos objetos depende del tipo de proyecto que esté desarrollando:  

-   En un proyecto de nivel de documento para Excel, use la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> de las clases `Sheet1`, `Sheet2`y `Sheet3` . Para obtener más información sobre estas clases, consulte [elemento Host Worksheet](../vsto/worksheet-host-item.md).  

-   En un proyecto de nivel de documento para Word, use la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la clase `ThisDocument` . Para obtener más información acerca de esta clase, vea [elemento Host Document](../vsto/document-host-item.md).  

-   En un proyecto de complemento de VSTO para Excel o Word, use la propiedad de los controles de un <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> que generan en tiempo de ejecución. Para obtener más información acerca de cómo generar estos objetos en tiempo de ejecución, consulte [ampliar documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="adding-controls"></a>Agregar controles  
 Los tipos <xref:Microsoft.Office.Tools.Excel.ControlCollection> y <xref:Microsoft.Office.Tools.Word.ControlCollection> incluyen métodos auxiliares que puede utilizar para agregar controles host y controles comunes de formularios Windows Forms a documentos y hojas de cálculo. Cada nombre de método tiene el formato `Add`*clase de control*, donde *clase de control* es el nombre de clase del control que quiere agregar. Por ejemplo, para agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> al documento, use el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .  

 En el ejemplo de código siguiente se agrega un elemento <xref:Microsoft.Office.Tools.Excel.NamedRange> a `Sheet1` un proyecto de nivel de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="accessing-and-deleting-controls"></a>Acceder a controles y eliminarlos  
 Puede usar la propiedad de los controles de un <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> para recorrer en iteración todos los controles del documento, incluidos los controles agregados en tiempo de diseño. Los controles que agregó en tiempo de diseño también se denominan *controles estáticos*.  

 Puede quitar controles dinámicos llamando al método de eliminación del control o llamando al método Remove de cada colección de controles. El siguiente ejemplo de código utiliza el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> para quitar un elemento <xref:Microsoft.Office.Tools.Excel.NamedRange> de `Sheet1` en un proyecto de nivel de documento para Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 No se pueden quitar controles estáticos en tiempo de ejecución. Si intenta utilizar el método Delete o quitar para quitar un control estático, un <xref:Microsoft.Office.Tools.CannotRemoveControlException> se iniciará.  

> [!NOTE]  
>  No quite controles mediante programación en el controlador de eventos `Shutdown` del documento. Los elementos de la interfaz de usuario del documento ya no estarán disponibles cuando se produzca el evento `Shutdown` . Si quiere quitar controles antes de que se cierre el documento, agregue el código al controlador de eventos de otro evento, como <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> o <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> para Word, o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> para Excel.  

##  <a name="HostControls"></a> Adding Host Controls to Documents  
 Cuando agregue controles host a documentos mediante programación, debe proporcionar un nombre que identifique de forma única el control y debe especificar en qué parte del documento se debe agregar el control. Para obtener instrucciones específicas, consulte los temas siguientes:  

-   [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Cómo: Agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Para más información sobre los controles host, consulte [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  

 Si un documento se guarda y después se cierra, todos los controles host creados dinámicamente se desconectan de sus eventos y pierden su funcionalidad de enlace de datos. Puede agregar código a la solución para volver a crear los controles host cuando se vuelva a abrir el documento. Para obtener más información, consulta [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  No se ofrecen métodos auxiliares para los siguientes controles host, debido a que estos controles no se pueden agregar mediante programación a documentos: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>y <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Adding Windows Forms Controls to Documents  
 Cuando se agrega mediante programación un control de formularios Windows Forms a un documento, debe proporcionar la ubicación del control y un nombre que lo identifique de forma única. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] proporciona métodos auxiliares para cada control. Estos métodos están sobrecargados para que pueda pasar un intervalo o coordenadas concretas para la ubicación del control.  

 Cuando un documento se guarda y se cierra, todos los controles de formularios Windows Forms creados dinámicamente se quitan del documento. Puede agregar código a la solución para volver a crear los controles cuando se vuelva a abrir el documento. Si crea controles dinámicos de formularios Windows Forms mediante el uso de un complemento de VSTO, los contenedores de ActiveX de los controles se dejan en el documento. Para obtener más información, consulta [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Los controles de formularios Windows Forms no se puede agregar mediante programación a documentos protegidos. Si desprotege mediante programación un documento de Word o una hoja de cálculo de Excel para agregar un control, debe escribir código adicional para quitar el contenedor de ActiveX del control cuando se cierre el documento. El contenedor de ActiveX del control no se elimina automáticamente de los documentos protegidos.  

### <a name="adding-custom-controls"></a>Agregar controles personalizados  
 Si quiere agregar un elemento <xref:System.Windows.Forms.Control> que no es compatible con los métodos auxiliares disponibles, como un control de usuario personalizado, use los métodos siguientes:  

-   En Excel, use uno de los métodos <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> de un objeto <xref:Microsoft.Office.Tools.Excel.ControlCollection> .  

-   En Word, use uno de los métodos <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> de un objeto <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

 Para agregar el control, pase el <xref:System.Windows.Forms.Control>, una ubicación para el control y un nombre que identifica de forma única el control al método AddControl. El método AddControl devuelve un objeto que define cómo interactúa el control con el documento o la hoja de cálculo. El método AddControl devuelve un <xref:Microsoft.Office.Tools.Excel.ControlSite> (para Excel) o un <xref:Microsoft.Office.Tools.Word.ControlSite> objeto (para Word).  

 En el ejemplo de código siguiente, se muestra cómo utilizar el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> para agregar dinámicamente un control de usuario personalizado a una hoja de cálculo en un proyecto de Excel de nivel de documento. En este ejemplo, el control de usuario se denomina `UserControl1`y el elemento <xref:Microsoft.Office.Interop.Excel.Range> se llama `range1`. Para usar este ejemplo, ejecútelo desde una clase `Sheet`*n* del proyecto.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="using-members-of-custom-controls"></a>Usar miembros de controles personalizados  
 Después de usar uno de los métodos de AddControl para agregar un control a una hoja de cálculo o documento, ahora tiene dos objetos de control diferentes:  

-   El objeto <xref:System.Windows.Forms.Control> que representa el control personalizado.  

-   El objeto ControlSite OLEObject y OLEControl que representa el control después de agregarlo a la hoja de cálculo o el documento.  

 Muchos métodos y propiedades se comparten entre estos controles. Es importante tener acceso a estos miembros a través del control adecuado:  

-   Para acceder a miembros que pertenezcan solo al control personalizado, use <xref:System.Windows.Forms.Control>.  

-   Para obtener acceso a miembros compartidos por los controles, utilice el objeto ControlSite OLEObject y OLEControl.  

 Si accede a un miembro compartido desde <xref:System.Windows.Forms.Control>, se podría producir un error sin advertencia ni notificación, o se pueden generar resultados no válidos. Utilice siempre métodos o propiedades del objeto ControlSite OLEObject y OLEControl a menos que el método o propiedad necesitado no está disponible; solo se debe hacer referencia el <xref:System.Windows.Forms.Control>.  

 Por ejemplo, tanto la <xref:Microsoft.Office.Tools.Excel.ControlSite> clase y la <xref:System.Windows.Forms.Control> clase tiene una propiedad superior. Para obtener o establecer la distancia entre la parte superior del control y la parte superior del documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> de <xref:Microsoft.Office.Tools.Excel.ControlSite>, no la propiedad <xref:System.Windows.Forms.Control.Top%2A> de <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Cómo: agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Cómo: agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
