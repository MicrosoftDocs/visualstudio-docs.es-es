---
title: "Enlazar datos a controles en soluciones de Office"
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
  - "documentos de Office [desarrollo de Office en Visual Studio], conexión a datos"
  - "datos, enlace de datos"
  - "enlace de datos"
  - "enlace de datos, soluciones de Office"
  - "enlace de datos, controles"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], enlace de datos"
  - "controles, enlace de datos"
ms.assetid: b6faaed7-df9b-4d78-9863-e515cd5c7ed9
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Enlazar datos a controles en soluciones de Office
  Puede enlazar controles de Windows Forms y *controles host* en un documento de Microsoft Office Word o una hoja de cálculo de Microsoft Office Excel a un origen de datos, de forma que los controles de muestren automáticamente los datos. Puede enlazar datos a controles en proyectos de nivel de aplicación y de nivel de documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Los controles host extienden objetos que están en los modelos de objetos de Word y Excel, como los controles de contenido de Word y los intervalos con nombre en Excel. Para obtener más información, consulta [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 Los controles de Windows Forms y host utilizan el modelo de enlace de datos de Windows Forms, que admite tanto *enlace de datos simple* como *enlace de datos complejo* a orígenes de datos como conjuntos de datos y tablas de datos. Para obtener información completa sobre el modelo de enlace de datos en Windows Forms, consulte [Enlace de datos y formularios Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
 ![vínculo a vídeo](~/data-tools/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: consumir datos de bases de datos en Excel](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## Enlace de datos simple  
 Un enlace de datos simple existe si un control de propiedad se enlaza a un único elemento de datos, como un valor de una tabla de datos. Por ejemplo, el control <xref:Microsoft.Office.Tools.Excel.NamedRange> tiene una propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> que se puede enlazar a un campo de un conjunto de datos. Cuando se cambia el campo del conjunto de datos, también cambia el valor del intervalo con nombre. Todos los controles host, excepto el control <xref:Microsoft.Office.Tools.Word.XMLNodes>, admiten el enlace de datos simple. El control <xref:Microsoft.Office.Tools.Word.XMLNodes> es una colección y, por tanto, no admite el enlace de datos.  
  
 Para realizar un enlace de datos simple a un control host, agregue un elemento <xref:System.Windows.Forms.Binding> a la propiedad DataBindings del control. Un objeto <xref:System.Windows.Forms.Binding> representa el enlace simple entre un valor de propiedad del control y el valor de un elemento de datos.  
  
 En el ejemplo siguiente se muestra cómo enlazar la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> a un elemento de datos en un proyecto de nivel de documento.  
  
 [!code-csharp[Trin_BindableComponent#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_BindableComponent/CS/Sheet1.cs#4)]
 [!code-vb[Trin_BindableComponent#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_BindableComponent/VB/Sheet1.vb#4)]  
  
 Para ver tutoriales que muestran el enlace de datos simple, consulte [Tutorial: Enlace de datos simple en un proyecto en el nivel del documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) para obtener un proyecto de nivel de documento y [Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) para ver un proyecto de complemento VSTO.  
  
## Enlace de datos complejo  
 El enlace de datos complejo existe cuando una propiedad de control está enlazada a más de un elemento de datos, como varias columnas de una tabla de datos. El control <xref:Microsoft.Office.Tools.Excel.ListObject> para Excel es el único control host que admite enlace de datos complejo. También hay muchos controles de Windows Forms que admiten enlace de datos complejo, como el control <xref:System.Windows.Forms.DataGridView>.  
  
 Para realizar el enlace de datos complejo, establezca la propiedad DataSource del control a un objeto de origen de datos que sea compatible con el enlace de datos complejo. Por ejemplo, la propiedad <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> del control <xref:Microsoft.Office.Tools.Excel.ListObject> puede estar enlazada a varias columnas de una tabla de datos. Todos los datos de la tabla de datos aparecen en el control <xref:Microsoft.Office.Tools.Excel.ListObject> y, como los datos de la tabla de datos cambian, el elemento <xref:Microsoft.Office.Tools.Excel.ListObject> también cambia. Para obtener una lista de los orígenes de datos que puede usar para el enlace de datos complejo, vea [Orígenes de datos compatibles con formularios Windows Forms](http://msdn.microsoft.com/library/3d2c43f6-462b-4d35-9c86-13e9afe012e1).  
  
 En el ejemplo de código siguiente se crea un elemento <xref:System.Data.DataSet> con dos objetos <xref:System.Data.DataTable> y se rellena una de las tablas con datos. El código enlaza después el elemento <xref:Microsoft.Office.Tools.Excel.ListObject> a la tabla que contiene datos. Este ejemplo es para un proyecto de nivel de documento de Excel.  
  
 [!code-csharp[Trin_ExcelListObject#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelListObject/CS/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelListObject/VB/Sheet1.vb#18)]  
  
 Para ver tutoriales que muestran el enlace de datos complejo, consulte [Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) para obtener un proyecto de nivel de documento y [Tutorial: enlace de datos complejos en el proyecto de complemento de VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) para ver un proyecto de complemento VSTO.  
  
## Visualización de datos en documentos y libros  
 En los proyectos de nivel de documento, puede utilizar la ventana **Orígenes de datos** para agregar controles enlazados a datos a los documentos o libros con facilidad, del mismo modo que los usa para Windows Forms. Para más información sobre el uso de la ventana **Orígenes de datos**, consulte [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md) y [Orígenes de datos &#40;ventana&#41;](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
### Arrastrar controles desde la ventana Orígenes de datos  
 Cuando se arrastra un objeto a un documento desde la ventana **Orígenes de datos**, se crea un control en el documento . El tipo de control que se crea depende de si se enlaza una única columna de datos o varias.  
  
 Para Excel, se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la hoja de cálculo para cada campo individual y un control <xref:Microsoft.Office.Tools.Excel.ListObject> para cada intervalo de datos que incluye varias filas y columnas. Puede cambiar este comportamiento predeterminado si selecciona la tabla o el campo en la ventana **Orígenes de datos** y elige un control diferente de la lista desplegable.  
  
 Se agrega un control <xref:Microsoft.Office.Tools.Word.ContentControl> a los documentos. El tipo del control de contenido depende del tipo de datos del campo que haya seleccionado.  
  
### Enlace de datos en proyectos de nivel de documento en tiempo de diseño  
 En los temas siguientes se muestran ejemplos de enlace de datos en tiempo de diseño:  
  
-   [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Cómo: Desplazarse por los registros de una base de datos en una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### Enlace de datos en proyectos de complemento de VSTO  
 En proyectos de complemento de VSTO, solo puede agregar controles en tiempo de ejecución. En los temas siguientes se muestran ejemplos de enlace de datos en tiempo de ejecución:  
  
-   [Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Tutorial: enlace de datos complejos en el proyecto de complemento de VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## Actualización de datos que están enlazados a controles host  
 El enlace de datos entre un origen de datos y un control host implica una actualización de datos bidireccional. En el enlace de datos simple, los cambios en el origen de datos se reflejan automáticamente en el control host, pero los cambios en el control host necesitan una llamada explícita para actualizar el origen de datos. La razón es que en algunos casos, los cambios en un campo enlazado a datos no se aceptan a menos que vayan acompañados de los cambios en otro campo enlazado a datos. Por ejemplo, podría tener dos campos, uno para la edad y otro para años de experiencia. La experiencia no puede superar la edad. Un usuario no puede actualizar la edad de 50 a 25 y, después, la experiencia de 30 a 10, a menos que realice los cambios al mismo tiempo. Para solucionar este problema, los campos con enlaces de datos simples no se actualizan hasta que las actualizaciones se envíen explícitamente mediante código.  
  
 Para actualizar un origen de datos a partir de controles host que habilitan un enlace de datos simple, debe enviar las actualizaciones al origen de datos en memoria \(como un elemento <xref:System.Data.DataSet> o <xref:System.Data.DataTable>\) y la base de datos back\-end si la solución utiliza una.  
  
 No es necesario actualizar explícitamente el origen de datos en memoria cuando se realiza el enlace de datos complejo mediante el control <xref:Microsoft.Office.Tools.Excel.ListObject>. En ese caso, los cambios se envían automáticamente al origen de datos en memoria sin nada de código adicional.  
  
 Para obtener más información, consulta [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Vea también  
 [Cómo: consumir datos de bases de datos en Excel](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Enlace de datos y formularios Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)   
 [Cómo: Crear un control con enlace simple en Windows Forms](http://msdn.microsoft.com/library/3bcaded8-0f1a-4cc0-8830-f59be253bf4e)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Guardar los datos en conjuntos de datos](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)  
  
  