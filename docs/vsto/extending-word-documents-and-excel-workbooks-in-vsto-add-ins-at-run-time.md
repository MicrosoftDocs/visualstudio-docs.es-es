---
title: Extender documentos de Word & libros de Excel en complementos de VSTO en tiempo de ejecución
description: Obtenga información acerca de cómo puede usar un complemento de VSTO para personalizar documentos de Word y libros de Excel de diversas maneras.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 465e28ed0c632bba45fac1670dd40cd90ef417f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970379"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución
  Puede utilizar un complemento de VSTO para personalizar documentos de Word y libros de Excel de las maneras siguientes:

- Agregar controles administrados a cualquier documento u hoja de cálculo abiertos.

- Convertir un objeto de lista existente de una hoja de cálculo de Excel en un <xref:Microsoft.Office.Tools.Excel.ListObject> extendido que expone eventos y que puede enlazarse a datos utilizando el modelo de enlace de datos de formularios Windows Forms.

- Obtener acceso a eventos de aplicación expuestos por Word y Excel para determinados documentos, libros y hojas de cálculo.

  Para utilizar esta funcionalidad, se genera un objeto en tiempo de ejecución que extienda el documento o libro.

  **Se aplica a:** La información de este artículo se aplica a los proyectos de complemento de VSTO para las siguientes aplicaciones: Excel y Word. Para obtener más información, consulte [características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generar objetos extendidos en complementos de VSTO
 Los *objetos extendidos* son instancias de tipos proporcionados por el runtime de Visual Studio Tools para Office que agregan funcionalidad a los objetos ya existentes de forma nativa en los modelos de objetos de Word o Excel (denominados *objetos nativos de Office*). Para generar un objeto extendido para un objeto de Word o Excel, use el método `GetVstoObject`. La primera vez que se llama al `GetVstoObject` método para un objeto de Word o Excel especificado, devuelve un nuevo objeto que extiende el objeto especificado. Cada vez que llame al método y especifique el mismo objeto de Word o Excel, devuelve el mismo objeto extendido.

 El tipo del objeto extendido tiene el mismo nombre que el tipo del objeto nativo de Office, pero este tipo está definido en el espacio de nombres <xref:Microsoft.Office.Tools.Excel> o <xref:Microsoft.Office.Tools.Word> . Por ejemplo, si se llama a la `GetVstoObject` método para extender un objeto <xref:Microsoft.Office.Interop.Word.Document>, el método devuelve un objeto <xref:Microsoft.Office.Tools.Word.Document>.

 Los métodos `GetVstoObject` se usan principalmente en proyectos de complementos VSTO. También puede utilizar estos métodos en proyectos de nivel de documento, pero se comportan de manera diferente y tienen menos usos.

 Para determinar si ya se ha generado un objeto extendido para un objeto nativo de Office determinado, use el método `HasVstoObject`. Para obtener más información, vea [determinar si un objeto de Office](#HasVstoObject)se ha extendido.

### <a name="generate-host-items"></a>Generar elementos host
 Cuando se usa `GetVstoObject` para extender un objeto de nivel de documento (es decir,, <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Word.Document> ), el objeto devuelto se denomina *elemento host*. Un elemento host es un tipo que puede contener otros objetos, incluidos otros controles y objetos extendidos. Se parece al tipo correspondiente del ensamblado de interoperabilidad primario de Word o Excel, pero tiene características adicionales. Para obtener más información sobre los elementos host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

 Después de generar un elemento host, se puede utilizar para agregar controles administrados al documento, libro u hoja de cálculo. Para obtener más información, vea [Agregar controles administrados a documentos y hojas de cálculo](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Para generar un elemento host para un documento de Word

- En el ejemplo de código siguiente se muestra cómo generar un elemento host para el documento activo.

     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Para generar un elemento host para un libro de Excel

- En el ejemplo de código siguiente se muestra cómo generar un elemento host para el libro activo.

     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Para generar un elemento host para una hoja de cálculo de Excel

- En el ejemplo de código siguiente se muestra cómo generar un elemento host para la hoja de cálculo activa en un proyecto.

     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]

### <a name="generate-listobject-host-controls"></a>Generar controles host ListObject
 Cuando se usa el método `GetVstoObject` para extender un <xref:Microsoft.Office.Interop.Excel.ListObject>, el método devuelve un <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject>Tiene todas las características de la original <xref:Microsoft.Office.Interop.Excel.ListObject> . También tiene funcionalidad adicional y se puede enlazar a datos utilizando el modelo de enlace de datos de Windows Forms. Para obtener más información, vea [ListObject (control](../vsto/listobject-control.md)).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Para generar un control host para un ListObject

- En el ejemplo de código siguiente se muestra cómo generar un <xref:Microsoft.Office.Tools.Excel.ListObject> para el primer <xref:Microsoft.Office.Interop.Excel.ListObject> de la hoja de cálculo activa en un proyecto.

     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Agregar controles administrados a documentos y hojas de cálculo
 Después de generar un <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet>, puede agregar controles al documento o la hoja de cálculo que representan estos objetos extendidos. Para agregar controles, use la `Controls` propiedad de <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> . Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Puede agregar controles de formularios Windows Forms o *controles host*. Un control host es un control proporcionado por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que encapsula el control correspondiente del ensamblado de interoperabilidad primario de Word o Excel. Un control host expone todo el comportamiento del objeto nativo de Office subyacente. También genera eventos y se puede enlazar a datos utilizando el modelo de enlace de datos de Windows Forms. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> No se puede agregar un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a una hoja de cálculo, ni un control <xref:Microsoft.Office.Tools.Word.XMLNode> o <xref:Microsoft.Office.Tools.Word.XMLNodes> a un documento mediante un complemento de VSTO. Estos controles host no pueden agregarse mediante programación. Para obtener más información, vea [limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Conservar y quitar controles
 Al agregar controles administrados a un documento o una hoja de cálculo, los controles no se conservan cuando se guarda y se cierra el documento. Se quitan todos los controles de host para que solo queden los objetos nativos subyacentes de Office. Por ejemplo, <xref:Microsoft.Office.Tools.Excel.ListObject> se convierte en <xref:Microsoft.Office.Interop.Excel.ListObject>. También se quitan todos los controles de formularios Windows Forms, pero los contenedores ActiveX de los controles se quedan en el documento. Debe incluir código en el complemento de VSTO para limpiar los controles o volver a crearlos la próxima vez que se abra el documento. Para obtener más información, vea [conservar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Obtener acceso a los eventos de nivel de aplicación en documentos y libros
 Algunos eventos de documento, libro y hoja de cálculo de los modelos de objetos nativos de Word y Excel solo se desencadenan en el nivel de aplicación. Por ejemplo, el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> se desencadena cuando se abre un documento de Word, pero este evento está definido en la clase <xref:Microsoft.Office.Interop.Word.Application> , en lugar de la clase <xref:Microsoft.Office.Interop.Word.Document> .

 Si usa únicamente objetos nativos de Office en el complemento de VSTO, debe controlar estos eventos en el nivel de aplicación y, a continuación, escribir código adicional para determinar si el documento que desencadenó el evento es un complemento que ha personalizado. Los elementos host proporcionan estos eventos en el nivel de documento para que resulte más fácil controlar los eventos de un documento específico. Puede generar un elemento host y, a continuación, controlar el evento para ese elemento host.

### <a name="example-that-uses-native-word-objects"></a>Ejemplo que utiliza objetos nativos de Word
 En el ejemplo de código siguiente se muestra cómo controlar un evento en el nivel de aplicación para los documentos de Word. El método `CreateDocument` crea un nuevo documento y, a continuación, define un controlador de eventos <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> que impide que se guarde este documento. El evento es un evento de nivel de aplicación que se genera para el <xref:Microsoft.Office.Interop.Word.Application> objeto y el controlador de eventos debe comparar el `Doc` parámetro con el `document1` objeto para determinar si `document1` representa el documento guardado.

 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]

### <a name="examples-that-use-a-host-item"></a>Ejemplos que utilizan un elemento host
 Los ejemplos de código siguientes simplifican este proceso controlando el evento <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> de un elemento host <xref:Microsoft.Office.Tools.Word.Document> . El `CreateDocument2` método de estos ejemplos genera un <xref:Microsoft.Office.Tools.Word.Document> que extiende el `document2` objeto y, a continuación, define un <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> controlador de eventos que impide que se guarde el documento. Solo se llama al controlador de eventos cuando `document2` se guarda y puede cancelar la acción de guardar sin realizar ningún trabajo adicional para comprobar qué documento se guardó.

 El siguiente ejemplo de código muestra esta tarea.

 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a> Determinar si un objeto de Office se ha extendido
 Para determinar si ya se ha generado un objeto extendido para un objeto nativo de Office determinado, use el método `HasVstoObject`. Este método devuelve **true** si ya se ha generado un objeto extendido.

 Utilice el método `Globals.Factory.HasVstoMethod`. Pase el objeto nativo de Word o Excel, como <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>, que desea probar para un objeto extendido.

 El método `HasVstoObject` resulta útil si desea ejecutar código solamente cuando un objeto de Office especificado tiene un objeto extendido. Por ejemplo, si tiene un complemento de VSTO de Word que controla el <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> evento para quitar controles administrados de un documento antes de guardarlo, utilice el `HasVstoObject` método para determinar si se ha extendido el documento. Si el documento no se ha extendido, no puede tener controles administrados y el controlador de eventos puede devolver sin intentar limpiar los controles del documento.

## <a name="see-also"></a>Vea también
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
