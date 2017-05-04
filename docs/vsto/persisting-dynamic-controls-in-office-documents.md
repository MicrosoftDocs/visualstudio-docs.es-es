---
title: "Guardar controles din&#225;micos en documentos de Office | Microsoft Docs"
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
  - "documentos de Office [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "documentos de Office [desarrollo de Office en Visual Studio], controles host"
  - "controles [desarrollo de Office en Visual Studio], guardar en el documento"
  - "controles de Windows Forms [desarrollo de Office en Visual Studio], guardar en el documento"
  - "documentos [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "documentos [desarrollo de Office en Visual Studio], controles host"
  - "controles host [desarrollo de Office en Visual Studio], guardar en el documento"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Guardar controles din&#225;micos en documentos de Office
  Los controles que se agregan en tiempo de ejecución no se conservan cuando se guarda y se cierra el documento o el libro. El comportamiento exacto es diferente para los controles host y los controles de Windows Forms. En ambos casos, puede agregar código a la solución para volver a crear los controles cuando el usuario vuelve a abrir el documento.  
  
 Los controles que agregue a los documentos en tiempo de ejecución se denominan *controles dinámicos*. Para más información sobre los controles dinámicos, consulte [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Guardar controles host en el documento  
 Cuando un documento se guarda y se cierra, todos los controles host dinámicos se quitan del documento. Solo los objetos de Office nativos subyacentes permanecen. Por ejemplo, un control host <xref:Microsoft.Office.Tools.Excel.ListObject> se convierte en un elemento <xref:Microsoft.Office.Interop.Excel.ListObject>. Los objetos de Office nativos no están conectados a los eventos de control host y no tienen la funcionalidad de enlace de datos del control host.  
  
 En la tabla siguiente se muestra el objeto de Office nativo que se deja en un documento para cada tipo de control host.  
  
|Tipo de control host|Tipo de objeto de Office nativo|  
|--------------------------|-------------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### Volver a crear controles host dinámicos cuando se abren documentos  
 Puede volver a crear controles host dinámicos en lugar de los controles nativos existentes cada vez que un usuario abre el documento. La creación de controles host de esta manera cuando se abre un documento simula la experiencia que podrían esperar los usuarios.  
  
 Para volver a crear un control host para Word, o un control host <xref:Microsoft.Office.Tools.Excel.NamedRange> o <xref:Microsoft.Office.Tools.Excel.ListObject> para Excel, use un método `Add`\<*clase de control*\> de un objeto <xref:Microsoft.Office.Tools.Excel.ControlCollection> o <xref:Microsoft.Office.Tools.Word.ControlCollection>. Utilice un método que tenga un parámetro para el objeto de Office nativo.  
  
 Por ejemplo, si quiere crear un control host <xref:Microsoft.Office.Tools.Excel.ListObject> desde un elemento <xref:Microsoft.Office.Interop.Excel.ListObject> nativo existente cuando se abre el documento, use el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> y pase el elemento <xref:Microsoft.Office.Interop.Excel.ListObject> existente. En el ejemplo de código siguiente esto se muestra en un proyecto de nivel de documento para Excel. El código vuelve a crear un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> dinámico que se basa en un elemento <xref:Microsoft.Office.Interop.Excel.ListObject> existente llamado `MyListObject` en la clase `Sheet1`.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### Volver a crear gráficos  
 Para volver a crear un control host <xref:Microsoft.Office.Tools.Excel.Chart>, primero debe eliminar el elemento <xref:Microsoft.Office.Interop.Excel.Chart> nativo y, después, volver a crear el elemento <xref:Microsoft.Office.Tools.Excel.Chart> mediante los métodos <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> o <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>. No hay ningún método `Add`\<*clase de control*\> que le permita crear un nuevo elemento <xref:Microsoft.Office.Tools.Excel.Chart> basado en un elemento <xref:Microsoft.Office.Interop.Excel.Chart> existente.  
  
 Si no elimina primero el elemento <xref:Microsoft.Office.Interop.Excel.Chart> nativo, creará un segundo gráfico duplicado al volver a crear el elemento <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## Guardar formularios Windows Forms en documentos  
 Cuando un documento se guarda y se cierra, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quita automáticamente todos los controles de formularios Windows Forms creados dinámicamente del documento. Sin embargo, el comportamiento es diferente para los proyectos de complemento de VSTO y de nivel de documento.  
  
 En las personalizaciones de nivel de documento, los controles y sus contenedores de ActiveX subyacentes \(que se utilizan para hospedar los controles en el documento\) se quitan la siguiente vez que se abra el documento. No hay ninguna indicación de que los controles estuvieran alguna vez ahí.  
  
 En los complementos de VSTO, los controles se quitan, pero los contenedores de ActiveX permanecen en el documento. La siguiente vez que el usuario abra el documento, los contenedores de ActiveX estarán visibles. En Excel, los contenedores de ActiveX muestran imágenes de los controles de la misma forma en que aparecían la última vez que se guardó el documento. En Word, los contenedores de ActiveX no están visibles a menos que el usuario haga clic en ellos, en cuyo caso muestran una línea de puntos que representa el borde de los controles. Hay varias formas de quitar los contenedores de ActiveX. Para más información, consulte [Quitar contenedores de ActiveX en un complemento](#removingActiveX).  
  
### Volver a crear controles de formularios Windows Forms cuando se abren documentos  
 Puede volver a crear los controles de formularios Windows Forms eliminados cuando el usuario vuelva a abrir el documento. Para ello, la solución debe realizar las siguientes tareas:  
  
1.  Almacenar información sobre el tamaño, la ubicación y el estado de los controles cuando se guarda o se cierra el documento. En una personalización de nivel de documento, puede guardar estos datos en la memoria caché de datos del documento. En un complemento VSTO, puede guardar estos datos en una parte XML personalizada del documento.  
  
2.  Volver a crear los controles en un evento que se genera cuando se abre el documento. En los proyectos de nivel de documento, puede hacerlo en los controladores de eventos `Sheet`*n*`_Startup` o `ThisDocument_Startup` En proyectos de complemento de VSTO, puede hacerlo en los controladores de eventos de los eventos <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
###  <a name="removingActiveX"></a> Quitar contenedores de ActiveX de un complemento  
 Cuando se agregan controles de formularios Windows Forms dinámicos a documentos mediante un complemento de VSTO, puede impedir que los contenedores de ActiveX de los controles aparezcan en el documento la siguiente vez que se abra, como se indica a continuación.  
  
#### Quitar contenedores de ActiveX cuando se abre el documento  
 Para quitar todos los contenedores de ActiveX, llame al método GetVstoObject para generar un elemento host para el elemento <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> que representa el documento recién abierto. Por ejemplo, para quitar todos los contenedores de ActiveX de un documento de Word, puede llamar al método GetVstoObject para generar un elemento host para el objeto <xref:Microsoft.Office.Interop.Word.Document> que se pasa al controlador de eventos del evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
 Este procedimiento es útil cuando se sabe que el documento solo se abrirá en equipos que tienen el complemento de VSTO instalado. Si cabe la posibilidad de que el documento se pase a otros usuarios que no tengan el complemento de VSTO instalado, considere en su lugar la posibilidad de quitar los controles antes de cerrar el documento.  
  
 En el ejemplo de código siguiente se muestra cómo llamar al método GetVstoObject cuando se abre el documento.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 Aunque el método GetVstoObject se utiliza principalmente para generar un nuevo elemento host en tiempo de ejecución, este método también borra todos los contenedores de ActiveX del documento la primera vez que se llama para un documento específico. Para más información sobre cómo usar el método GetVstoObject, consulte [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Tenga en cuenta que si el complemento de VSTO crea controles dinámicos cuando se abre el documento, el complemento de VSTO ya llamará al método GetVstoObject como parte del proceso para crear los controles. No es necesario agregar una llamada independiente al método GetVstoObject para quitar los contenedores de ActiveX en este escenario.  
  
#### Quitar los controles dinámicos antes de que se cierre el documento  
 El complemento de VSTO puede quitar explícitamente cada uno de los controles dinámicos del documento antes de que se cierre. Este procedimiento es útil para los documentos que podrían pasarse a otros usuarios que no tienen el complemento de VSTO instalado.  
  
 En el ejemplo de código siguiente se muestra cómo quitar todos los controles de formularios Windows Forms de un documento de Word cuando se cierra el documento.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## Vea también  
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  