---
title: "Cómo: actualizar un origen de datos con datos de un Control Host | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fd4716e81d280e049a8cbd1a5206b52f2714e27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Cómo: Actualizar un origen de datos con datos de un control Host
  Puede enlazar un control host a un origen de datos y actualizar el origen de datos con los cambios que se realicen en los datos del control. Hay dos pasos principales en este proceso:  
  
1.  Actualizar el origen de datos en memoria con los datos modificados en el control. Normalmente, el origen de datos en memoria es un elemento <xref:System.Data.DataSet>, un elemento <xref:System.Data.DataTable>, u otro objeto de datos.  
  
2.  Actualizar la base de datos con los datos modificados en el origen de datos en memoria. Esto solo es aplicable si el origen de datos está conectado a una base de datos back-end, como una base de datos de SQL Server o Microsoft Office Access.  
  
 Para obtener más información sobre controles host y el enlace de datos, vea [elementos Host y la información general sobre controles de Host](../vsto/host-items-and-host-controls-overview.md) y [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="updating-the-in-memory-data-source"></a>Actualización del origen de datos en memoria  
 De forma predeterminada, los controles host que habilitan el enlace de datos simple (como los controles de contenido en un documento de Word o un control de intervalo con nombre en una hoja de cálculo de Excel) no guardan los cambios de datos en el origen de datos en memoria. Es decir, cuando un usuario final cambia un valor en un control host y después se desplaza fuera del control, el nuevo valor del control no se guarda automáticamente en el origen de datos.  
  
 Para guardar los datos en el origen de datos, puede escribir código que actualice el origen de datos como respuesta a un evento concreto en tiempo de ejecución o puede configurar el control para que actualice automáticamente el origen de datos cuando el valor en el control cambie.  
  
 No es necesario guardar los cambios de <xref:Microsoft.Office.Tools.Excel.ListObject> en el origen de datos en memoria. Cuando se enlaza un control <xref:Microsoft.Office.Tools.Excel.ListObject> a los datos, el control <xref:Microsoft.Office.Tools.Excel.ListObject> guarda automáticamente los cambios en el origen de datos en memoria sin necesidad de código adicional.  
  
#### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Para actualizar el origen de datos en memoria en tiempo de ejecución  
  
-   Llame al método <xref:System.Windows.Forms.Binding.WriteValue%2A> del objeto <xref:System.Windows.Forms.Binding> que enlaza el control al origen de datos.  
  
     En el ejemplo siguiente se guardan los cambios realizados a un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en una hoja de cálculo de Excel en el origen de datos. En este ejemplo se supone que tiene un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `namedRange1` con su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> enlazada a un campo de un origen de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-updating-the-in-memory-data-source"></a>Actualización automática del origen de datos en memoria  
 También puede configurar un control para que actualice automáticamente el origen de datos en memoria. En un proyecto de nivel de documento, puede hacerlo mediante código o con el diseñador. En un proyecto de complemento de VSTO, debe utilizar código.  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Para establecer un control que actualice automáticamente el origen de datos en memoria mediante código  
  
1.  Usar el modo System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged de la <xref:System.Windows.Forms.Binding> objeto que enlaza el control al origen de datos. Hay dos opciones para actualizar el origen de datos:  
  
    -   Para actualizar el origen de datos cuando se valida el control, establezca esta propiedad en System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Para actualizar el origen de datos cuando cambia el valor de la propiedad enlazada a datos del control, establezca esta propiedad en System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  La opción System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged no se aplica a controles host de Word porque Word no notificaciones no oferta de documento o cambio de control. Sin embargo, esta opción puede utilizarse para los controles de Windows Forms en documentos de Word.  
  
     En el ejemplo siguiente se configura un control <xref:Microsoft.Office.Tools.Excel.NamedRange> que actualiza automáticamente el origen de datos cuando cambia el valor en el control. En este ejemplo se supone que tiene un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `namedRange1` con su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> enlazada a un campo de un origen de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Para establecer un control a fin de que actualice automáticamente el origen de datos en memoria mediante el diseñador  
  
1.  En Visual Studio, abra el documento de Word o el libro de Excel en el diseñador.  
  
2.  Haga clic en el control que desea que actualice automáticamente el origen de datos.  
  
3.  En la ventana **Propiedades** , expanda la propiedad **(DataBindings)** .  
  
4.  Junto a la **(avanzado)** propiedad, haga clic en el botón de puntos suspensivos (![de pantalla de VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "de pantalla de VisualStudioEllipsesButton")).  
  
5.  En el cuadro de diálogo **Formato y enlace de datos avanzado** , haga clic en la lista desplegable **Modo de actualización del origen de datos** y seleccione uno de los siguientes valores:  
  
    -   Para actualizar el origen de datos cuando se valida el control, seleccione **OnValidation**.  
  
    -   Para actualizar el origen de datos cuando cambia el valor de la propiedad enlazada a datos del control, seleccione **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  La opción **OnPropertyChanged** no se aplica a los controles host de Word porque Word no ofrece notificaciones de cambios de documento o de control. Sin embargo, esta opción puede utilizarse para los controles de Windows Forms en documentos de Word.  
  
6.  Cierre el cuadro de diálogo **Formato y enlace de datos avanzado** .  
  
## <a name="updating-the-database"></a>Actualizar la base de datos  
 Si el origen de datos en memoria está asociado a una base de datos, debe actualizar la base de datos con los cambios en el origen de datos. Para obtener más información acerca de cómo actualizar una base de datos, vea [guardar los datos en la base de datos](../data-tools/save-data-back-to-the-database.md) y [actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
#### <a name="to-update-the-database"></a>Para actualizar la base de datos  
  
1.  Llame al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del elemento <xref:System.Windows.Forms.BindingSource> para el control.  
  
     El elemento <xref:System.Windows.Forms.BindingSource> se genera automáticamente cuando agrega un control enlazado a datos a un documento o un libro en tiempo de diseño. El elemento <xref:System.Windows.Forms.BindingSource> conecta el control al conjunto de datos con tipo en el proyecto. Para obtener más información, consulta [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     En el siguiente ejemplo se supone que el proyecto contiene un elemento <xref:System.Windows.Forms.BindingSource> denominado `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Llame a la `Update` método del TableAdapter generado en el proyecto.  
  
     Lo TableAdapter se genera automáticamente cuando se agrega un control enlazado a datos a un documento o libro en tiempo de diseño. Lo TableAdapter conecta el conjunto de datos con tipo en el proyecto a la base de datos. Para obtener más información, consulta [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     El ejemplo de código siguiente se da por supuesto que tiene una conexión a la tabla Customers en la base de datos Northwind y que el proyecto contiene un TableAdapter llamado `customersTableAdapter` y un conjunto de datos con tipo denominado `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Guardar datos en la base de datos](../data-tools/save-data-back-to-the-database.md)    
 [Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Cómo: desplazarse por registros de base de datos en una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  