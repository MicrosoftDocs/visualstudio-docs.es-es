---
title: "Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecuci&#243;n"
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
  - "GetVstoObject (método)"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], agregar controles a los documentos"
  - "elementos host [desarrollo de Office en Visual Studio], crear  complementos en tiempo de ejecución"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], extender documentos de Word"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], extender libros de Excel"
  - "controles [desarrollo de Office en Visual Studio], agregar durante el tiempo de ejecución"
  - "HasVstoObject (método)"
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecuci&#243;n
  Puede utilizar un complemento de VSTO para personalizar documentos de Word y libros de Excel de las maneras siguientes:  
  
-   Agregar controles administrados a cualquier documento u hoja de cálculo abiertos.  
  
-   Convertir un objeto de lista existente de una hoja de cálculo de Excel en un <xref:Microsoft.Office.Tools.Excel.ListObject> extendido que expone eventos y que puede enlazarse a datos utilizando el modelo de enlace de datos de formularios Windows Forms.  
  
-   Obtener acceso a eventos de aplicación expuestos por Word y Excel para determinados documentos, libros y hojas de cálculo.  
  
 Para utilizar esta funcionalidad, se genera un objeto en tiempo de ejecución que extienda el documento o libro.  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de complementos de VSTO para las siguientes aplicaciones: Excel y Word. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Generar objetos extendidos en complementos de VSTO  
 Los *objetos extendidos* son instancias de tipos proporcionados por el runtime de Visual Studio Tools para Office que agregan funcionalidad a los objetos ya existentes de forma nativa en los modelos de objetos de Word o Excel \(denominados *objetos nativos de Office*\). Para generar un objeto extendido para un objeto de Word o Excel, use el método GetVstoObject. La primera vez que llame al método GetVstoObject para objeto especificado de Word o Excel, devuelve un nuevo objeto que extiende el objeto especificado. Cada vez que llame al método y especifique el mismo objeto de Word o Excel, devuelve el mismo objeto extendido.  
  
 El tipo del objeto extendido tiene el mismo nombre que el tipo del objeto nativo de Office, pero este tipo está definido en el espacio de nombres <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word>. Por ejemplo, si se llama a la GetVstoObject método para extender un objeto <xref:Microsoft.Office.Interop.Word.Document>, el método devuelve un objeto <xref:Microsoft.Office.Tools.Word.Document>.  
  
 Los métodos GetVstoObject se usan principalmente en proyectos de complementos VSTO. También puede utilizar estos métodos en proyectos de nivel de documento, pero se comportan de manera diferente y tienen menos usos.  
  
 Para determinar si ya se ha generado un objeto extendido para un objeto nativo de Office determinado, use el método HasVstoObject. Para obtener más información, vea el artículo sobre [determinar si un objeto de Office se ha extendido](#HasVstoObject).  
  
### Generar elementos host  
 Cuando se utiliza GetVstoObject para ampliar un objeto de nivel de documento \(es decir, un <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Word.Document>\), el objeto devuelto se denomina *elemento host*. Un elemento host es un tipo que puede contener otros objetos, incluidos otros controles y objetos extendidos. Se parece al tipo correspondiente del ensamblado de interoperabilidad primario de Word o Excel, pero tiene características adicionales. Para obtener más información sobre los elementos host, consulte [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 Después de generar un elemento host, se puede utilizar para agregar controles administrados al documento, libro u hoja de cálculo. Para más información, vea [Agregar controles administrados a documentos y hojas de cálculo](#AddControls).  
  
##### Para generar un elemento host para un documento de Word  
  
-   En el ejemplo de código siguiente se muestra cómo generar un elemento host para el documento activo.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_WordAddInDynamicControls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#8)]  
  
##### Para generar un elemento host para un libro de Excel  
  
-   En el ejemplo de código siguiente se muestra cómo generar un elemento host para el libro activo.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
##### Para generar un elemento host para una hoja de cálculo de Excel  
  
-   En el ejemplo de código siguiente se muestra cómo generar un elemento host para la hoja de cálculo activa en un proyecto.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
### Generar controles host ListObject  
 Cuando se usa el método GetVstoObject para extender un <xref:Microsoft.Office.Interop.Excel.ListObject>, el método devuelve un <xref:Microsoft.Office.Tools.Excel.ListObject>. El <xref:Microsoft.Office.Tools.Excel.ListObject> tiene todas las características del <xref:Microsoft.Office.Interop.Excel.ListObject> original, pero también tiene funcionalidad adicional, como la capacidad de enlazar a datos utilizando el modelo de enlace de datos de formularios Windows Forms. Para obtener más información, consulta [ListObject &#40;Control&#41;](../vsto/listobject-control.md).  
  
##### Para generar un control host para un ListObject  
  
-   En el ejemplo de código siguiente se muestra cómo generar un <xref:Microsoft.Office.Tools.Excel.ListObject> para el primer <xref:Microsoft.Office.Interop.Excel.ListObject> de la hoja de cálculo activa en un proyecto.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
##  <a name="AddControls"></a> Agregar controles administrados a documentos y hojas de cálculo  
 Después de generar un <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet>, puede agregar controles al documento o la hoja de cálculo que representan estos objetos extendidos. Para hacerlo, use la propiedad Controls de <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet>. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Puede agregar controles de formularios Windows Forms o *controles host*. Un control host es un control proporcionado por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que encapsula el control correspondiente del ensamblado de interoperabilidad primario de Word o Excel. Un control host expone todo el comportamiento del objeto nativo de Office subyacente, pero también desencadena eventos y se puede enlazar a datos utilizando el modelo de enlace de datos de formularios Windows Forms. Para obtener más información, consulta [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  No se puede agregar un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a una hoja de cálculo, ni un control <xref:Microsoft.Office.Tools.Word.XMLNode> o <xref:Microsoft.Office.Tools.Word.XMLNodes> a un documento mediante un complemento de VSTO. Estos controles host no pueden agregarse mediante programación. Para obtener más información, consulta [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Conservar y quitar controles  
 Al agregar controles administrados a un documento o una hoja de cálculo, los controles no se conservan cuando se guarda y se cierra el documento. Se quitan todos los controles de host para que solo queden los objetos nativos subyacentes de Office. Por ejemplo, <xref:Microsoft.Office.Tools.Excel.ListObject> se convierte en <xref:Microsoft.Office.Interop.Excel.ListObject>. También se quitan todos los controles de formularios Windows Forms, pero los contenedores ActiveX de los controles se quedan en el documento. Debe incluir código en el complemento de VSTO para limpiar los controles o volver a crearlos la próxima vez que se abra el documento. Para obtener más información, consulta [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## Obtener acceso a los eventos en el nivel de aplicación en documentos y libros  
 Algunos eventos de documento, libro y hoja de cálculo de los modelos de objetos nativos de Word y Excel solo se desencadenan en el nivel de aplicación. Por ejemplo, el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> se desencadena cuando se abre un documento de Word, pero este evento está definido en la clase <xref:Microsoft.Office.Interop.Word.Application>, en lugar de la clase <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Si usa únicamente objetos nativos de Office en el complemento de VSTO, debe controlar estos eventos en el nivel de aplicación y, a continuación, escribir código adicional para determinar si el documento que desencadenó el evento es un complemento que ha personalizado. Los elementos host proporcionan estos eventos en el nivel de documento para que resulte más fácil controlar los eventos de un documento específico. Puede generar un elemento host y, a continuación, controlar el evento para ese elemento host.  
  
### Ejemplo que utiliza objetos nativos de Word  
 En el ejemplo de código siguiente se muestra cómo controlar un evento en el nivel de aplicación para los documentos de Word. El método `CreateDocument` crea un nuevo documento y, a continuación, define un controlador de eventos <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> que impide que se guarde este documento. Puesto que se trata de un evento en el nivel de aplicación que se desencadena para el objeto <xref:Microsoft.Office.Interop.Word.Application>, el controlador de eventos debe comparar el parámetro `Doc` con el objeto `document1` para determinar si `document1` representa el documento guardado.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#12)]
 [!code-vb[Trin_WordAddInDynamicControls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#12)]  
  
### Ejemplos que utilizan un elemento host  
 Los ejemplos de código siguientes simplifican este proceso controlando el evento <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> de un elemento host <xref:Microsoft.Office.Tools.Word.Document>. El método `CreateDocument2` de estos ejemplos genera un <xref:Microsoft.Office.Tools.Word.Document> que extiende el objeto `document2` y, a continuación, define un controlador de eventos <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> que evita que se guarde el documento. Dado que solo se llama a este controlador de eventos cuando se guarda `document2`, el controlador de eventos puede cancelar la acción sin tener que realizar ningún trabajo adicional para comprobar qué documento se guardó.  
  
 El siguiente ejemplo de código muestra esta tarea.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#13)]
 [!code-vb[Trin_WordAddInDynamicControls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#13)]  
  
##  <a name="HasVstoObject"></a> Determinar si un objeto de Office se ha extendido  
 Para determinar si ya se ha generado un objeto extendido para un objeto nativo de Office determinado, use el método HasVstoObject. Este método devuelve **true** si ya se ha generado un objeto extendido; en caso contrario, devuelve **false**.  
  
 Utilice el método Globals.Factory.HasVstoMethod. Pase el objeto nativo de Word o Excel, como <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>, que desea probar para un objeto extendido.  
  
 El método HasVstoObject resulta útil si desea ejecutar código solamente cuando un objeto de Office especificado tiene un objeto extendido. Por ejemplo, si tiene un complemento de VSTO de Word que controla el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> para quitar controles administrados de un documento antes de que se guarde, puede utilizar el método HasVstoObject para determinar si se ha extendido el documento. Si no se ha extendido el documento, no puede contener controles administrados y, por tanto, el controlador de eventos puede simplemente volver sin intentar limpiar los controles del documento.  
  
## Vea también  
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)  
  
  