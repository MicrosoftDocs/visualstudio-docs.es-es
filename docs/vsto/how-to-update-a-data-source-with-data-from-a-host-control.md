---
title: "C&#243;mo: Actualizar un origen de datos con datos de un control Host"
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
  - "documentos [desarrollo de Office en Visual Studio], actualizaciones de origen de datos"
  - "datos [desarrollo de Office en Visual Studio], actualización de un origen de datos desde un documento"
  - "controles host [desarrollo de Office en Visual Studio], actualizaciones de origen de datos"
  - "documentos de Office [desarrollo de Office en Visual Studio, orígenes de datos"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# C&#243;mo: Actualizar un origen de datos con datos de un control Host
  Puede enlazar un control host a un origen de datos y actualizar el origen de datos con los cambios que se realicen en los datos del control. Hay dos pasos principales en este proceso:  
  
1.  Actualizar el origen de datos en memoria con los datos modificados en el control. Normalmente, el origen de datos en memoria es un elemento <xref:System.Data.DataSet>, un elemento <xref:System.Data.DataTable>, u otro objeto de datos.  
  
2.  Actualizar la base de datos con los datos modificados en el origen de datos en memoria. Esto solo es aplicable si el origen de datos está conectado a una base de datos back\-end, como una base de datos de SQL Server o Microsoft Office Access.  
  
 Para más información sobre los controles host y el enlace de datos, consulte [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md) y [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Actualización del origen de datos en memoria  
 De forma predeterminada, los controles host que habilitan el enlace de datos simple \(como los controles de contenido en un documento de Word o un control de intervalo con nombre en una hoja de cálculo de Excel\) no guardan los cambios de datos en el origen de datos en memoria. Es decir, cuando un usuario final cambia un valor en un control host y después se desplaza fuera del control, el nuevo valor del control no se guarda automáticamente en el origen de datos.  
  
 Para guardar los datos en el origen de datos, puede escribir código que actualice el origen de datos como respuesta a un evento concreto en tiempo de ejecución o puede configurar el control para que actualice automáticamente el origen de datos cuando el valor en el control cambie.  
  
 No es necesario guardar los cambios de <xref:Microsoft.Office.Tools.Excel.ListObject> en el origen de datos en memoria. Cuando se enlaza un control <xref:Microsoft.Office.Tools.Excel.ListObject> a los datos, el control <xref:Microsoft.Office.Tools.Excel.ListObject> guarda automáticamente los cambios en el origen de datos en memoria sin necesidad de código adicional.  
  
#### Para actualizar el origen de datos en memoria en tiempo de ejecución  
  
-   Llame al método <xref:System.Windows.Forms.Binding.WriteValue%2A> del objeto <xref:System.Windows.Forms.Binding> que enlaza el control al origen de datos.  
  
     En el ejemplo siguiente se guardan los cambios realizados a un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en una hoja de cálculo de Excel en el origen de datos. En este ejemplo se supone que tiene un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `namedRange1` con su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> enlazada a un campo de un origen de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### Actualización automática del origen de datos en memoria  
 También puede configurar un control para que actualice automáticamente el origen de datos en memoria. En un proyecto de nivel de documento, puede hacerlo mediante código o con el diseñador. En un proyecto de complemento de VSTO, debe utilizar código.  
  
##### Para establecer un control que actualice automáticamente el origen de datos en memoria mediante código  
  
1.  Utilice el modo System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  del objeto <xref:System.Windows.Forms.Binding> que enlaza el control al origen de datos. Hay dos opciones para actualizar el origen de datos:  
  
    -   Para actualizar el origen de datos cuando se valida el control, establezca esta propiedad en System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Para actualizar el origen de datos cuando cambia el valor de la propiedad enlazada a datos del control, establezca esta propiedad en System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  La opción System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged no se aplica a controles host de Word porque Word no ofrece notificaciones de cambios de documento o de control. Sin embargo, esta opción puede utilizarse para los controles de Windows Forms en documentos de Word.  
  
     En el ejemplo siguiente se configura un control <xref:Microsoft.Office.Tools.Excel.NamedRange> que actualiza automáticamente el origen de datos cuando cambia el valor en el control. En este ejemplo se supone que tiene un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `namedRange1` con su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> enlazada a un campo de un origen de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### Para establecer un control a fin de que actualice automáticamente el origen de datos en memoria mediante el diseñador  
  
1.  En Visual Studio, abra el documento de Word o el libro de Excel en el diseñador.  
  
2.  Haga clic en el control que desea que actualice automáticamente el origen de datos.  
  
3.  En la ventana **Propiedades**, expanda la propiedad **\(DataBindings\)**.  
  
4.  Junto a la propiedad **\(Avanzado\)**, haga clic en el botón de puntos suspensivos \(![Captura de pantalla de VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "Captura de pantalla de VisualStudioEllipsesButton")\).  
  
5.  En el cuadro de diálogo **Formato y enlace de datos avanzado**, haga clic en la lista desplegable **Modo de actualización del origen de datos** y seleccione uno de los siguientes valores:  
  
    -   Para actualizar el origen de datos cuando se valida el control, seleccione **OnValidation**.  
  
    -   Para actualizar el origen de datos cuando cambia el valor de la propiedad enlazada a datos del control, seleccione **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  La opción **OnPropertyChanged** no se aplica a los controles host de Word porque Word no ofrece notificaciones de cambios de documento o de control. Sin embargo, esta opción puede utilizarse para los controles de Windows Forms en documentos de Word.  
  
6.  Cierre el cuadro de diálogo **Formato y enlace de datos avanzado**.  
  
## Actualizar la base de datos  
 Si el origen de datos en memoria está asociado a una base de datos, debe actualizar la base de datos con los cambios en el origen de datos. Para más información sobre cómo actualizar una base de datos, vea [Guardar los datos en conjuntos de datos](../Topic/Saving%20data%20back%20to%20the%20database.md) y [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
#### Para actualizar la base de datos  
  
1.  Llame al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del elemento <xref:System.Windows.Forms.BindingSource> para el control.  
  
     El elemento <xref:System.Windows.Forms.BindingSource> se genera automáticamente cuando agrega un control enlazado a datos a un documento o un libro en tiempo de diseño. El elemento <xref:System.Windows.Forms.BindingSource> conecta el control al conjunto de datos con tipo en el proyecto. Para obtener más información, consulta [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
     En el siguiente ejemplo se supone que el proyecto contiene un elemento <xref:System.Windows.Forms.BindingSource> denominado `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  Llame al método `Update` del elemento TableAdapter generado en su proyecto.  
  
     El elemento TableAdapter se genera automáticamente cuando agrega un control enlazado a datos a un documento o un libro en tiempo de diseño. El elemento TableAdapter conecta el conjunto de datos con tipo del proyecto a la base de datos. Para obtener más información, consulta [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     En el ejemplo de código siguiente se supone que dispone de una conexión a la tabla Customers de la base de datos Northwind y que el proyecto contiene un elemento TableAdapter denominado `customersTableAdapter` y un conjunto de datos con tipo denominado `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Guardar los datos en conjuntos de datos](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Cómo: Desplazarse por los registros de una base de datos en una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  