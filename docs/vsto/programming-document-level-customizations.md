---
title: Programar personalizaciones de nivel de documento | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a614173fc33547c3512c031b7e0bd8a5575e7cb2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="programming-document-level-customizations"></a>Programar personalizaciones de nivel de documento
  Al ampliar Microsoft Office Word o Microsoft Office Excel mediante una personalización de nivel de documento, puede realizar las siguientes tareas:  
  
-   Automatizar la aplicación mediante su modelo de objetos.  
  
-   Agregar controles en la superficie del documento.  
  
-   Llamar al código de Visual Basic para aplicaciones (VBA) en el documento desde el ensamblado de personalización.  
  
-   Llamar al código en el ensamblado de personalización desde VBA.  
  
-   Administrar determinados aspectos del documento mientras se encuentra en un servidor que no tiene instalado Microsoft Office.  
  
-   Personalizar la interfaz de usuario (UI) de la aplicación.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Algunos aspectos de la escritura de código en proyectos de nivel de documento difieren de otros tipos de proyectos de Visual Studio. Muchas de estas diferencias se deben a la forma en que los modelos de objetos de Office se exponen al código administrado. Para obtener más información, consulta [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
 Para obtener información general sobre las personalizaciones de nivel de documento y otros tipos de soluciones que puede crear mediante el uso de las herramientas de desarrollo de Office en Visual Studio, vea [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>Usar las clases generadas en proyectos de nivel de documento  
 Cuando crea un proyecto de nivel de documento, Visual Studio crea automáticamente una clase en el proyecto que puede usar para comenzar a escribir el código. Visual Studio crea diferentes clases para Word y Excel:  
  
-   En los proyectos de nivel de documento de Word, la clase se denomina `ThisDocument` de forma predeterminada.  
  
-   En cambio, los proyectos de nivel de documento de Excel tienen creadas varias clases: una para el propio libro y una para cada hoja de cálculo. Estas clases se denominan de la siguiente manera, de forma predeterminada:  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 La clase creada incluye controladores de eventos a los que se llama cuando el documento está abierto o cerrado. Para ejecutar el código cuando se abre el documento, agregue ese código al controlador de eventos `Startup` . Para ejecutar el código justo antes de cerrar el documento, agregue ese código al controlador de eventos `Shutdown` . Para obtener más información, consulta [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>Información acerca del diseño de las clases creadas  
 En aquellos proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], los tipos de elementos host que se encuentran en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] son interfaces, por lo que las clases creadas no pueden derivar su implementación de ellas. En su lugar, las clases creadas derivan la mayoría de sus miembros de las siguientes clases base:  
  
-   `ThisDocument`: deriva de <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
-   `ThisWorkbook`: deriva de <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
-   `Sheet` *n*: deriva de <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
 Estas clases base redirigen todas las llamadas realizadas a sus miembros, a las implementaciones internas de las correspondientes interfaces de elementos host del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por ejemplo, si llama al método <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> de la clase `ThisDocument` , la clase <xref:Microsoft.Office.Tools.Word.DocumentBase> redirige esta llamada a la implementación interna de la interfaz de <xref:Microsoft.Office.Tools.Word.Document> en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>Obtener acceso al modelo de objetos de la aplicación host  
 Para obtener acceso al modelo de objetos de la aplicación host, use los miembros de la clase generada en el proyecto. Cada una de esas clases corresponde a un objeto del modelo de objetos de Excel o de Word y contiene en su mayoría las mismas propiedades, métodos y eventos. Por ejemplo, la clase `ThisDocument` de un proyecto de nivel de documento de Word proporciona en su mayoría los mismos miembros que el objeto <xref:Microsoft.Office.Interop.Word.Document> del modelo de objetos de Word.  
  
 En el ejemplo de código siguiente se muestra cómo usar el modelo de objetos de Word para guardar el documento que forma parte de una personalización de nivel de documento de Word.  Este ejemplo está pensado para ejecutarse desde la clase `ThisDocument` .  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Para hacer lo mismo desde fuera de la clase `ThisDocument` , use el objeto `Globals` para tener acceso a la clase `ThisDocument` . Por ejemplo, puede agregar este código a un archivo de código del panel de acciones si desea incluir el botón **Guardar** en la interfaz de usuario del panel de acciones.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Dado que la clase `ThisDocument` obtiene la mayoría de sus miembros del elemento host <xref:Microsoft.Office.Tools.Word.Document> , el método `Save` al que se llama en este código es de hecho el método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> del elemento host <xref:Microsoft.Office.Tools.Word.Document> . Este método corresponde al método <xref:Microsoft.Office.Interop.Word._Document.Save%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> en el modelo de objetos de Word.  
  
 Para obtener más información acerca del uso de los modelos de objetos de Word y Excel, consulte [Word Object Model Overview](../vsto/word-object-model-overview.md) y [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 Para obtener más información sobre la `Globals` de objetos, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="adding-controls-to-documents"></a>Agregar controles a documentos  
 Para personalizar la interfaz de usuario del documento, puede agregar controles de Windows Forms o *controles host* a la superficie del documento. Si combina diferentes conjuntos de controles y escribe código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario.  
  
 Los controles host son clases que extienden algunos de los objetos de los modelos de objetos de Word y Excel. Por ejemplo, el control host <xref:Microsoft.Office.Tools.Excel.ListObject> proporciona toda la funcionalidad del elemento <xref:Microsoft.Office.Interop.Excel.ListObject> en Excel. Sin embargo, el control host <xref:Microsoft.Office.Tools.Excel.ListObject> también tiene eventos adicionales y funciones de enlace de datos.  
  
 Para obtener más información, vea [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="combining-vba-and-document-level-customizations"></a>Combinar personalizaciones de VBA y de nivel de documento  
 Puede usar código de VBA en un documento que forma parte de una personalización de nivel de documento Asimismo, también puede llamar al código VBA del documento desde el ensamblado de personalización, y configurar el proyecto de modo que permita que el código VBA del documento llame al código del ensamblado de personalización.  
  
 Para obtener más información, consulta [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="managing-documents-on-a-server"></a>Administrar documentos en un servidor  
 Puede administrar diferentes aspectos de las personalizaciones de nivel de documento en un servidor que no tenga Microsoft Office Word o Microsoft Office Excel instalado. Por ejemplo, puede obtener acceso y modificar los datos en la caché de datos del documento. Asimismo, también puede administrar el ensamblado de personalización asociado al documento. Por ejemplo, puede quitar mediante programación el ensamblado del documento para que este no ejecute el código, o bien puede asociar mediante programación un ensamblado a un documento.  
  
 Para obtener más información, consulta [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Personalizar la interfaz de usuario de las aplicaciones de Microsoft Office  
 Puede personalizar la interfaz de usuario de Word y Excel de las siguientes maneras, mediante una personalización de nivel de documento:  
  
-   Agregar controles host o controles de Windows Forms a la superficie del documento.  
  
     Para obtener más información, vea [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md), [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)y [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Agregar un panel de acciones al documento.  
  
     Para obtener más información, consulta [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Agregar pestañas personalizadas a la cinta.  
  
     Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Agregar grupos personalizados a una pestaña integrada en la cinta.  
  
     Para obtener más información, consulta [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md).  
  
 Para obtener más información acerca de cómo personalizar las aplicaciones de interfaz de usuario de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Obtener objetos extendidos de los objetos de Office nativos en personalizaciones de nivel de documento  
 Muchos controladores de eventos de Office reciben un objeto de Office nativo que representa el libro, la hoja de cálculo o el documento que provocó el evento. En algunos casos, le puede interesar ejecutar cierto código, solo si el libro o el documento de la personalización de nivel del documento provocó el evento. Por ejemplo, en una personalización de nivel de documento de Excel, le podría interesar ejecutar el código cuando el usuario activa una de las hojas de cálculo del libro personalizado, pero no cuando el usuario activa una hoja de cálculo en algún otro libro que esté abierto al mismo tiempo que el primero.  
  
 Si tiene un objeto de Office nativo, puede probar si ese objeto se ha extendido en un *elemento host* o en un *control host* de una personalización de nivel de documento. Los elementos host y los controles host son tipos que proporciona [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , y que agregan funcionalidad a los objetos que existen de forma nativa en los modelos de objetos de Excel o Word (denominados *objetos de Office nativos*). En conjunto, los elementos host y los controles host también se denominan *objetos extendidos*. Para obtener más información sobre los elementos host y los controles host, consulte [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>Información acerca de los métodos GetVstoObject y HasVstoObject  
 Para probar un objeto de Office nativo, use los métodos HasVstoObject y GetVstoObject en el proyecto:  
  
-   Utilice el método HasVstoObject si desea determinar si el objeto de Office nativo tiene un objeto extendido en la personalización. Este método devuelve **true** si el objeto de Office nativo tiene un objeto extendido, y **false** si no lo tiene.  
  
-   Utilice el método GetVstoObject si desea obtener el objeto extendido para un objeto de Office nativo. Este método devuelve un objeto <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>o <xref:Microsoft.Office.Tools.Word.Document> si el objeto de Office nativo especificado tiene uno. En caso contrario, devuelve GetVstoObject **null**. Por ejemplo, se devuelve el método GetVstoObject un <xref:Microsoft.Office.Tools.Word.Document> si especificado <xref:Microsoft.Office.Interop.Word.Document> es el objeto subyacente para el documento en el proyecto de documento de Word.  
  
 En los proyectos de nivel de documento, no puede usar el método GetVstoObject para crear un nuevo <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, o <xref:Microsoft.Office.Tools.Word.Document> elemento host en tiempo de ejecución. Solo puede usar este método para tener acceso a los elementos host existentes creados en el proyecto en tiempo de diseño. Si desea crear nuevos elementos host en tiempo de ejecución, debe desarrollar un proyecto de complemento VSTO. Para obtener más información, vea [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) y [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>Usar los métodos GetVstoObject y HasVstoObject  
 Para llamar al método GetVstoObject y HasVstoObject, use el método Globals.Factory.GetVstoObject o Globals.Factory.HasVstoObject y pase el objeto nativo de Word o Excel (como un <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>) que desea probar.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  