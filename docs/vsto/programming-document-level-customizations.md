---
title: "Programar personalizaciones de nivel de documento | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Sheet3"
  - "thisWorkbook"
  - "thisDocument"
  - "Sheet1"
  - "Sheet2"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ThisDocument (clase)"
  - "Sheet3 (clase)"
  - "ThisWorkbook (clase)"
  - "escribir código para soluciones de Office"
  - "programación [desarrollo de Office en Visual Studio], personalizaciones de nivel de documento"
  - "Sheet1 (clase)"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], personalizaciones de nivel de documento"
  - "Sheet2 (clase)"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], programación"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], personalizaciones de nivel de documento"
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Programar personalizaciones de nivel de documento
  Al ampliar Microsoft Office Word o Microsoft Office Excel mediante una personalización de nivel de documento, puede realizar las siguientes tareas:  
  
-   Automatizar la aplicación mediante su modelo de objetos.  
  
-   Agregar controles en la superficie del documento.  
  
-   Llamar al código de Visual Basic para aplicaciones \(VBA\) en el documento desde el ensamblado de personalización.  
  
-   Llamar al código en el ensamblado de personalización desde VBA.  
  
-   Administrar determinados aspectos del documento mientras se encuentra en un servidor que no tiene instalado Microsoft Office.  
  
-   Personalizar la interfaz de usuario \(UI\) de la aplicación.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Algunos aspectos de la escritura de código en proyectos de nivel de documento difieren de otros tipos de proyectos de Visual Studio. Muchas de estas diferencias se deben a la forma en que los modelos de objetos de Office se exponen al código administrado. Para obtener más información, consulta [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md).  
  
 Para obtener información general acerca de las personalizaciones de nivel de documento y otros tipos de soluciones que puede crear con las herramientas de desarrollo de Office en Visual Studio, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Usar las clases generadas en proyectos de nivel de documento  
 Cuando crea un proyecto de nivel de documento, Visual Studio crea automáticamente una clase en el proyecto que puede usar para comenzar a escribir el código. Visual Studio crea diferentes clases para Word y Excel:  
  
-   En los proyectos de nivel de documento de Word, la clase se denomina `ThisDocument` de forma predeterminada.  
  
-   En cambio, los proyectos de nivel de documento de Excel tienen creadas varias clases: una para el propio libro y una para cada hoja de cálculo. Estas clases se denominan de la siguiente manera, de forma predeterminada:  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 La clase creada incluye controladores de eventos a los que se llama cuando el documento está abierto o cerrado. Para ejecutar el código cuando se abre el documento, agregue ese código al controlador de eventos `Startup`. Para ejecutar el código justo antes de cerrar el documento, agregue ese código al controlador de eventos `Shutdown`. Para obtener más información, consulta [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
### Información acerca del diseño de las clases creadas  
 En aquellos proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], los tipos de elementos host que se encuentran en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] son interfaces, por lo que las clases creadas no pueden derivar su implementación de ellas. En su lugar, las clases creadas derivan la mayoría de sus miembros de las siguientes clases base:  
  
-   `ThisDocument`: deriva de <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
-   `ThisWorkbook`: deriva de <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
-   `Sheet` *n*: deriva de <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
 Estas clases base redirigen todas las llamadas realizadas a sus miembros, a las implementaciones internas de las correspondientes interfaces de elementos host del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por ejemplo, si llama al método <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> de la clase `ThisDocument`, la clase <xref:Microsoft.Office.Tools.Word.DocumentBase> redirige esta llamada a la implementación interna de la interfaz de <xref:Microsoft.Office.Tools.Word.Document> en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## Obtener acceso al modelo de objetos de la aplicación host  
 Para obtener acceso al modelo de objetos de la aplicación host, use los miembros de la clase generada en el proyecto. Cada una de esas clases corresponde a un objeto del modelo de objetos de Excel o de Word y contiene en su mayoría las mismas propiedades, métodos y eventos. Por ejemplo, la clase `ThisDocument` de un proyecto de nivel de documento de Word proporciona en su mayoría los mismos miembros que el objeto <xref:Microsoft.Office.Interop.Word.Document> del modelo de objetos de Word.  
  
 En el ejemplo de código siguiente se muestra cómo usar el modelo de objetos de Word para guardar el documento que forma parte de una personalización de nivel de documento de Word.  Este ejemplo está pensado para ejecutarse desde la clase `ThisDocument`.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Para hacer lo mismo desde fuera de la clase `ThisDocument`, use el objeto `Globals` para tener acceso a la clase `ThisDocument`. Por ejemplo, puede agregar este código a un archivo de código del panel de acciones si desea incluir el botón **Guardar** en la interfaz de usuario del panel de acciones.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Dado que la clase `ThisDocument` obtiene la mayoría de sus miembros del elemento host <xref:Microsoft.Office.Tools.Word.Document>, el método `Save` al que se llama en este código es de hecho el método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> del elemento host <xref:Microsoft.Office.Tools.Word.Document>. Este método corresponde al método <xref:Microsoft.Office.Interop.Word._Document.Save%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> en el modelo de objetos de Word.  
  
 Para obtener más información acerca del uso de los modelos de objetos de Word y Excel, consulte [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md) y [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
 Para obtener más información sobre del objeto `Globals`, consulte [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## Agregar controles a documentos  
 Para personalizar la interfaz de usuario del documento, puede agregar controles de Windows Forms o *controles host* a la superficie del documento. Si combina diferentes conjuntos de controles y escribe código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario.  
  
 Los controles host son clases que extienden algunos de los objetos de los modelos de objetos de Word y Excel. Por ejemplo, el control host <xref:Microsoft.Office.Tools.Excel.ListObject> proporciona toda la funcionalidad del elemento <xref:Microsoft.Office.Interop.Excel.ListObject> en Excel. Sin embargo, el control host <xref:Microsoft.Office.Tools.Excel.ListObject> también tiene eventos adicionales y funciones de enlace de datos.  
  
 Para obtener más información, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md) y [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Combinar personalizaciones de VBA y de nivel de documento  
 Puede usar código de VBA en un documento que forma parte de una personalización de nivel de documento Asimismo, también puede llamar al código VBA del documento desde el ensamblado de personalización, y configurar el proyecto de modo que permita que el código VBA del documento llame al código del ensamblado de personalización.  
  
 Para obtener más información, consulta [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## Administrar documentos en un servidor  
 Puede administrar diferentes aspectos de las personalizaciones de nivel de documento en un servidor que no tenga Microsoft Office Word o Microsoft Office Excel instalado. Por ejemplo, puede obtener acceso y modificar los datos en la caché de datos del documento. Asimismo, también puede administrar el ensamblado de personalización asociado al documento. Por ejemplo, puede quitar mediante programación el ensamblado del documento para que este no ejecute el código, o bien puede asociar mediante programación un ensamblado a un documento.  
  
 Para obtener más información, consulta [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## Personalizar la interfaz de usuario de las aplicaciones de Microsoft Office  
 Puede personalizar la interfaz de usuario de Word y Excel de las siguientes maneras, mediante una personalización de nivel de documento:  
  
-   Agregar controles host o controles de Windows Forms a la superficie del documento.  
  
     Para obtener más información, vea [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md), [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md) y [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Agregar un panel de acciones al documento.  
  
     Para obtener más información, consulta [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
-   Agregar pestañas personalizadas a la cinta.  
  
     Para obtener más información, consulta [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Agregar grupos personalizados a una pestaña integrada en la cinta.  
  
     Para obtener más información, consulta [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).  
  
 Para obtener más información acerca de cómo personalizar las aplicaciones de interfaz de usuario de Microsoft Office, consulte [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Obtener objetos extendidos de los objetos de Office nativos en personalizaciones de nivel de documento  
 Muchos controladores de eventos de Office reciben un objeto de Office nativo que representa el libro, la hoja de cálculo o el documento que provocó el evento. En algunos casos, le puede interesar ejecutar cierto código, solo si el libro o el documento de la personalización de nivel del documento provocó el evento. Por ejemplo, en una personalización de nivel de documento de Excel, le podría interesar ejecutar el código cuando el usuario activa una de las hojas de cálculo del libro personalizado, pero no cuando el usuario activa una hoja de cálculo en algún otro libro que esté abierto al mismo tiempo que el primero.  
  
 Si tiene un objeto de Office nativo, puede probar si ese objeto se ha extendido en un *elemento host* o en un *control host* de una personalización de nivel de documento. Los elementos host y los controles host son tipos que proporciona [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], y que agregan funcionalidad a los objetos que existen de forma nativa en los modelos de objetos de Excel o Word \(denominados *objetos de Office nativos*\). En conjunto, los elementos host y los controles host también se denominan *objetos extendidos*. Para obtener más información sobre los elementos host y los controles host, consulte [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
## Información acerca de los métodos GetVstoObject y HasVstoObject  
 Para probar un objeto de Office nativo, use los métodos HasVstoObject y GetVstoObject del proyecto:  
  
-   Use el método HasVstoObject si desea determinar si el objeto de Office nativo tiene un objeto extendido en la personalización. Este método devuelve **true** si el objeto de Office nativo tiene un objeto extendido, y **false** si no lo tiene.  
  
-   Use el método GetVstoObject si desea obtener el objeto extendido de un objeto de Office nativo. Este método devuelve un objeto <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> si el objeto de Office nativo especificado tiene uno. De lo contrario, GetVstoObject devuelve **null**. Por ejemplo, el método GetVstoObject devuelve un <xref:Microsoft.Office.Tools.Word.Document> si el <xref:Microsoft.Office.Interop.Word.Document> especificado es el objeto subyacente del documento que se encuentra en el proyecto de documento de Word.  
  
 En los proyectos de nivel de documento, no se puede usar el método GetVstoObject para crear un nuevo elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución. Solo puede usar este método para tener acceso a los elementos host existentes creados en el proyecto en tiempo de diseño. Si desea crear nuevos elementos host en tiempo de ejecución, debe desarrollar un proyecto de complemento VSTO. Para obtener más información, vea [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) y [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Usar los métodos GetVstoObject y HasVstoObject  
 Para llamar a los métodos HasVstoObject y GetVstoObject, use el método Globals.Factory.GetVstoObject o Globals.Factory.HasVstoObject y, a continuación, pase el objeto nativo de Word o Excel \(como <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>\) que desee probar.  
  
## Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  