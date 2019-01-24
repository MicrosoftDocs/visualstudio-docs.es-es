---
title: Guardar controles dinámicos en documentos de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 570131dfdb3cb582ba6ee6c8a12fff2dfcc01e98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894800"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Guardar controles dinámicos en documentos de Office

Los controles que se agregan en tiempo de ejecución no se conservan cuando se guarda y se cierra el documento o libro. El comportamiento exacto es diferente para los controles host y los controles de Windows Forms. En ambos casos, puede agregar código a la solución para volver a crear los controles cuando el usuario vuelve a abrir el documento.

Los controles que agregue a los documentos en tiempo de ejecución se denominan *controles dinámicos*. Para obtener más información sobre los controles dinámicos, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Conservar los controles host en el documento

Cuando un documento se guarda y se cierra, todos los controles host dinámicos se quitan del documento. Solo los objetos de Office nativos subyacentes permanecen. Por ejemplo, un control host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> se convierte en un elemento <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Los objetos de Office nativos no están conectados a los eventos de control host y no tienen la funcionalidad de enlace de datos del control host.

En la tabla siguiente se muestra el objeto de Office nativo que se deja en un documento para cada tipo de control host.

|Tipo de control host|Tipo de objeto de Office nativo|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Volver a crear controles host dinámicos cuando se abren documentos

Puede volver a crear controles host dinámicos en lugar de los controles nativos existentes cada vez que un usuario abre el documento. La creación de controles host de esta manera cuando se abre un documento simula la experiencia que podrían esperar los usuarios.

Para volver a crear un control host para Word, o un <xref:Microsoft.Office.Tools.Excel.NamedRange> o <xref:Microsoft.Office.Tools.Excel.ListObject> control host para Excel, use un `Add` \< *clase control*> método de un <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> o <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> objeto. Utilice un método que tenga un parámetro para el objeto de Office nativo.

Por ejemplo, si quiere crear un control host <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> desde un elemento <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> nativo existente cuando se abre el documento, use el método <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> y pase el elemento <xref:Microsoft.Office.Interop.Excel.ListObject>existente. En el ejemplo de código siguiente esto se muestra en un proyecto de nivel de documento para Excel. El código vuelve a crear un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> dinámico que se basa en un elemento <xref:Microsoft.Office.Interop.Excel.ListObject> existente llamado `MyListObject` en la clase `Sheet1` .

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Volver a crear el gráfico

Para volver a crear un <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> hospedar el control, primero debe eliminar nativo <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>y, a continuación, volver a crear la <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> utilizando el <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> método. No hay ningún `Add` \< *clase control*> método que le permite crear un nuevo <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> basado en un <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>.

Si no elimina primero nativo <xref:Microsoft.Office.Interop.Excel.Chart>, a continuación, creará un segundo gráfico duplicado al volver a crear la <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>.

## <a name="persist-windows-forms-controls-in-documents"></a>Conservar los controles de Windows Forms en documentos

Cuando un documento se guarda y se cierra, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quita automáticamente todos los controles de formularios Windows Forms creados dinámicamente del documento. Sin embargo, el comportamiento es diferente para los proyectos de complemento de VSTO y de nivel de documento.

En las personalizaciones de nivel de documento, los controles y sus contenedores de ActiveX subyacentes (que se utilizan para hospedar los controles en el documento) se quitan la siguiente vez que se abra el documento. No hay ninguna indicación de que los controles estuvieran alguna vez ahí.

En los complementos de VSTO, los controles se quitan, pero los contenedores de ActiveX permanecen en el documento. La siguiente vez que el usuario abra el documento, los contenedores de ActiveX estarán visibles. En Excel, los contenedores de ActiveX muestran imágenes de los controles de la misma forma en que aparecían la última vez que se guardó el documento. En Word, los contenedores de ActiveX no están visibles a menos que el usuario haga clic en ellos, en cuyo caso muestran una línea de puntos que representa el borde de los controles. Hay varias formas de quitar los contenedores de ActiveX. Para obtener más información, consulte [quitar contenedores de ActiveX en un complemento](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Volver a crear controles de formularios Windows Forms cuando se abren documentos

Puede volver a crear los controles de formularios Windows Forms eliminados cuando el usuario vuelva a abrir el documento. Para ello, la solución debe realizar las siguientes tareas:

1.  Almacenar información sobre el tamaño, la ubicación y el estado de los controles cuando se guarda o se cierra el documento. En una personalización de nivel de documento, puede guardar los datos a la caché de datos en el documento. En un complemento de VSTO, puede guardar los datos a un elemento XML personalizado en el documento.

2.  Volver a crear los controles en un evento que se genera cuando se abre el documento. En los proyectos de nivel de documento, puede hacerlo en los controladores de eventos `Sheet`*n*`_Startup` o `ThisDocument_Startup` En proyectos de complemento de VSTO, puede hacerlo en los controladores de eventos de los eventos <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

###  <a name="removingActiveX"></a> Quitar contenedores de ActiveX en un complemento

Al agregar controles de Windows Forms dinámicos a documentos mediante el uso de un complemento de VSTO, puede impedir que los contenedores de ActiveX para los controles que aparecen en el documento la próxima vez que se abre en las siguientes maneras.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Quitar contenedores de ActiveX cuando se abre el documento

Para quitar todos los contenedores de ActiveX, llame al método `GetVstoObject` para generar un elemento host para el elemento <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> que representa el documento recién abierto. Por ejemplo, para quitar todos los contenedores de ActiveX de un documento de Word, puede llamar al método `GetVstoObject` para generar un elemento host para el objeto <xref:Microsoft.Office.Interop.Word.Document> que se pasa al controlador de eventos del evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.

Este procedimiento es útil cuando se sabe que el documento solo se abrirá en equipos que tienen el complemento de VSTO instalado. Si cabe la posibilidad de que el documento se pase a otros usuarios que no tengan el complemento de VSTO instalado, considere en su lugar la posibilidad de quitar los controles antes de cerrar el documento.

En el ejemplo de código siguiente se muestra cómo llamar al método `GetVstoObject` cuando se abre el documento.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Aunque el `GetVstoObject` método se utiliza principalmente para generar un nuevo elemento host en tiempo de ejecución, este método también borra todos los contenedores de ActiveX del documento de la primera vez que se llama para un documento específico. Para obtener más información sobre cómo usar el `GetVstoObject` método, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Si su complemento VSTO crea controles dinámicos cuando se abre el documento, los complementos de VSTO ya llamará el `GetVstoObject` método como parte del proceso para crear los controles. No es necesario agregar una llamada independiente al método `GetVstoObject` para quitar los contenedores de ActiveX en este escenario.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Quitar los controles dinámicos antes de cerrar el documento

El complemento de VSTO puede quitar explícitamente cada uno de los controles dinámicos del documento antes de que se cierre. Este procedimiento es útil para los documentos que podrían pasarse a otros usuarios que no tienen el complemento de VSTO instalado.

En el ejemplo de código siguiente se muestra cómo quitar todos los controles de formularios Windows Forms de un documento de Word cuando se cierra el documento.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Vea también

- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
