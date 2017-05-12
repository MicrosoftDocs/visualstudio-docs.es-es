---
title: "ListObject (Control)"
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
  - "VST.Toolbox.List"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "listas, eventos"
  - "ListObject (control)"
  - "Control ListObject, eventos"
  - "Control ListObject, enlace de datos"
  - "Control ListObject, mejorar el rendimiento cuando está enlazado a datos"
ms.assetid: 2bdecbf0-2a0f-48de-a544-dca12bb4a9a3
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# ListObject (Control)
  El control <xref:Microsoft.Office.Tools.Excel.ListObject> es una lista que expone eventos y se puede enlazar a datos. Al agregar una lista a una hoja de cálculo, Visual Studio crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> que se puede programar directamente sin tener que recorrer el modelo de objetos de Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Crear el control  
 En proyectos de nivel de documento, puede agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> a la hoja de cálculo en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO, puede agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> a hojas de cálculo solo en tiempo de ejecución. Para obtener más información, consulta [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  De forma predeterminada, los objetos de lista creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Enlazar datos al control  
 Un control <xref:Microsoft.Office.Tools.Excel.ListObject> admite el enlace de datos simple y complejo. El control <xref:Microsoft.Office.Tools.Excel.ListObject> se puede enlazar a un origen de datos mediante las propiedades <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> y <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> en tiempo de diseño o el método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> en tiempo de ejecución.  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Excel.ListObject> se actualiza automáticamente cuando se enlaza a un origen de datos, como un <xref:System.Data.DataTable>, que genera eventos cuando cambian los datos. Si enlaza el <xref:Microsoft.Office.Tools.Excel.ListObject> a un origen de datos que no provoca eventos cuando cambian los datos, se debe llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> o <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> para actualizar <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Cuando se agrega un <xref:Microsoft.Office.Tools.Excel.ListObject> a una celda de la hoja de cálculo asignando un elemento de esquema repetitivo a esa celda, Visual Studio asigna automáticamente <xref:Microsoft.Office.Tools.Excel.ListObject> al conjunto de datos generado. Sin embargo, <xref:Microsoft.Office.Tools.Excel.ListObject> no se enlaza automáticamente a los datos. Puede tomar medidas para enlazar <xref:Microsoft.Office.Tools.Excel.ListObject> al conjunto de datos en tiempo de diseño o en tiempo de ejecución en un proyecto de nivel de documento. Puede enlazar mediante programación <xref:Microsoft.Office.Tools.Excel.ListObject> al conjunto de datos en tiempo de ejecución en un complemento VSTO.  
  
 Dado que los datos están separados de <xref:Microsoft.Office.Tools.Excel.ListObject>, debe agregar y quitar los datos a través del conjunto de datos enlazado y no directamente a través de <xref:Microsoft.Office.Tools.Excel.ListObject>. Si los datos del conjunto de datos enlazado se actualizan mediante cualquier mecanismo, el control <xref:Microsoft.Office.Tools.Excel.ListObject> refleja los cambios. Para obtener más información, consulta [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Puede rellenar rápidamente un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazando el <xref:Microsoft.Office.Tools.Excel.ListObject> a un origen de datos. Si edita los datos en un enlace de datos <xref:Microsoft.Office.Tools.Excel.ListObject>, los cambios también se realizan automáticamente en el origen de datos. Si desea rellenar un <xref:Microsoft.Office.Tools.Excel.ListObject> y permitir al usuario cambiar los datos de <xref:Microsoft.Office.Tools.Excel.ListObject> sin modificar el origen de datos, puede utilizar el método <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> para desasociar el <xref:Microsoft.Office.Tools.Excel.ListObject> del origen de datos. Para obtener más información, consulta [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  El enlace de datos no se admite en superposición de controles <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
### Mejorar el rendimiento en controles ListObject  
 La lectura de un archivo XML en un control <xref:Microsoft.Office.Tools.Excel.ListObject> de enlace de datos tiende a ser más lenta si se enlaza primero el control y luego se llama a <xref:System.Data.DataSet.ReadXml%2A> para rellenar el conjunto de datos. Para mejorar el rendimiento, llame a <xref:System.Data.DataSet.ReadXml%2A> antes de enlazar el control.  
  
### Desconectar controles ListObject del origen de datos  
 Después de rellenar un control <xref:Microsoft.Office.Tools.Excel.ListObject> con datos mediante el enlace a un origen de datos, puede desconectarlo para que las modificaciones realizadas en los datos del objeto de lista no afecten al origen de datos. Para obtener más información, consulta [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### Restaurar el orden de columnas y filas  
 Cuando se enlazan datos a un control <xref:Microsoft.Office.Tools.Excel.ListObject> que se ha agregado a un documento en tiempo de diseño, Visual Studio realiza un seguimiento del orden de columnas y filas cada vez que se guarde el libro. Si un usuario mueve las columnas o filas de <xref:Microsoft.Office.Tools.Excel.ListObject> durante el tiempo de ejecución, se conservará el orden nuevo la próxima vez que se abra el libro y el control <xref:Microsoft.Office.Tools.Excel.ListObject> se enlazará al origen de datos nuevo.  
  
 Si desea restaurar <xref:Microsoft.Office.Tools.Excel.ListObject> a su orden original de columnas y filas, puede llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A>. Este método quita las propiedades de documento personalizadas relacionadas con el orden de columnas y filas especificado en <xref:Microsoft.Office.Tools.Excel.ListObject>. Llame a este método desde el evento <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> del libro si no desea conservar el orden de columnas y filas de <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## Formato  
 El formato que puede aplicarse a un control <xref:Microsoft.Office.Interop.Excel.ListObject> también puede aplicarse a un control <xref:Microsoft.Office.Tools.Excel.ListObject>. Esto incluye bordes, fuentes, formato de número y estilos. Los usuarios finales pueden reorganizar las columnas en un enlace de datos <xref:Microsoft.Office.Tools.Excel.ListObject>, y estos cambios se conservarán con el documento, siempre que el <xref:Microsoft.Office.Tools.Excel.ListObject> se haya agregado al documento en tiempo de diseño. La próxima vez que se abre el documento, el objeto de lista se enlazará al mismo origen de datos, pero el orden de las columnas reflejará los cambios de los usuarios.  
  
## Agregar y quitar columnas en tiempo de ejecución  
 No puede agregar o quitar manualmente columnas en un control <xref:Microsoft.Office.Tools.Excel.ListObject> de datos enlazados en tiempo de ejecución. Si un usuario final intenta eliminar una columna, inmediatamente se restaurará y se quitarán las columnas agregadas. Por lo tanto, es importante escribir código para explicar a los usuarios por qué no pueden realizar estas acciones en un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a datos. Visual Studio proporciona varios eventos en un <xref:Microsoft.Office.Tools.Excel.ListObject> relacionado con el enlace de datos. Por ejemplo, puede usar el evento <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> para avisar a los usuarios de que no se pueden eliminar los datos que han intentado eliminar y que se han restaurado.  
  
## Agregar y quitar filas en tiempo de ejecución  
 Puede agregar y quitar manualmente filas en un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazado a datos, siempre que el origen de datos permita la adición de nuevas filas y no sea de solo lectura. Puede escribir código para los eventos, como <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>, para validar los datos. Para obtener más información, consulta [Cómo: Validar datos cuando se agrega una fila nueva a un control ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 A veces, la relación del objeto de lista al origen de datos produce errores de rutina. Por ejemplo, puede asignar las columnas que desea que aparezcan en el <xref:Microsoft.Office.Tools.Excel.ListObject>, por lo que si omite columnas con restricciones, como un campo que no puede aceptar valores null, se producen errores cada vez que se crea una fila. Puede escribir código para agregar los valores que faltan en un controlador de eventos para el evento <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>.  
  
## Cambiar el nombre de los controles ListObject en Excel  
 Excel permite a los usuarios cambiar el nombre de las tablas de Excel en tiempo de ejecución mediante la pestaña **Diseño**. Sin embargo, el control <xref:Microsoft.Office.Tools.Excel.ListObject> no es compatible con esta característica. Si un usuario intenta cambiar el nombre de una tabla de Excel que corresponde a un <xref:Microsoft.Office.Tools.Excel.ListObject>, el nombre de la tabla de Excel se revertirá automáticamente al nombre original cuando se guarde el libro.  
  
## Eventos  
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Excel.ListObject>:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## Vea también  
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Cómo: Validar datos cuando se agrega una fila nueva a un control ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Cómo: Asignar columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  