---
title: Procedimiento Guardar documentos mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 965f8d9661d30d23365fe324f7102e15fafec77c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056281"
---
# <a name="how-to-programmatically-save-documents"></a>Procedimiento Guardar documentos mediante programación
  Hay varias maneras de guardar documentos de Microsoft Office Word. Puede guardar un documento sin cambiar el nombre del documento, o puede guardar un documento con un nombre nuevo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Guardar un documento sin cambiar el nombre

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Para guardar el documento asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Para guardar el documento activo

1. Llame a la <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método para el documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Si no está seguro de si el documento que desea guardar es el documento activo, puede hacer referencia a él por su nombre.

### <a name="to-save-a-document-specified-by-name"></a>Para guardar el documento especificado por nombre

1. Utilice el nombre del documento como argumento a la <xref:Microsoft.Office.Interop.Word.Documents> colección. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre
 Utilice el método SaveAs para guardar el documento con un nombre nuevo. Puede usar este método para el <xref:Microsoft.Office.Tools.Word.Document> elemento de host en un proyecto de nivel de documento de Word o de nativo <xref:Microsoft.Office.Interop.Word.Document> objeto en cualquier proyecto de Word. Este método requiere que especifique el nuevo nombre de archivo, pero otros argumentos son opcionales.

> [!NOTE]
>  Si se muestra el **SaveAs** cuadro de diálogo dentro de la <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> controlador de eventos de `ThisDocument` y establezca el *cancelar* parámetro **false**, es posible que la aplicación cerrar inesperadamente. Si establece la *cancelar* parámetro **true**, aparecerá un error que indica que se ha deshabilitado el autoguardado.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Para guardar el documento asociado a una personalización de nivel de documento con un nuevo nombre

1. Llame a la <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método de la `ThisDocument` clase del proyecto, mediante una ruta de acceso y un nombre completo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` .

    > [!NOTE]
    >  El <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método produce una excepción si no existe un directorio de destino o si hay otro problema al guardar un archivo. Es recomendable usar un **try... catch** bloquear en torno a la <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> método o dentro de un método que realiza la llamada.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Para guardar un documento nativo con un nuevo nombre

1. Llame a la <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método de la <xref:Microsoft.Office.Interop.Word.Document> que desea guardar, mediante una ruta de acceso y un nombre completo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.

     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    > [!NOTE]
    >  El <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método produce una excepción si no existe un directorio de destino o si hay otro problema al guardar un archivo. Es recomendable usar un **try... catch** bloquear en torno a la <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método o dentro de un método que realiza la llamada.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Para guardar un documento por su nombre, un documento llamado *NewDocument.doc* debe existir en un directorio denominado *prueba* en la unidad C.

- Para guardar un documento con un nuevo nombre, un directorio denominado *prueba* debe existir en la unidad C.

## <a name="see-also"></a>Vea también
- [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elemento host Document](../vsto/document-host-item.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
