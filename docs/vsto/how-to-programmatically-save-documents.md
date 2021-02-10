---
title: 'Cómo: guardar documentos mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para guardar un documento mediante programación sin cambiar el nombre del documento o con un nombre nuevo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 34992bb4f76f68229bebbdb98265838f049dc288
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949784"
---
# <a name="how-to-programmatically-save-documents"></a>Cómo: guardar documentos mediante programación

Hay varias maneras de guardar Microsoft Office documentos de Word. Puede guardar un documento sin cambiar el nombre del documento o puede guardar un documento con un nombre nuevo.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Guardar un documento sin cambiar el nombre

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Para guardar el documento asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Para guardar el documento activo

1. Llame al <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método para el documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Si no está seguro de si el documento que desea guardar es el documento activo, puede hacer referencia a él por su nombre.

### <a name="to-save-a-document-specified-by-name"></a>Para guardar un documento especificado por su nombre

1. Use el nombre del documento como argumento para la <xref:Microsoft.Office.Interop.Word.Documents> colección. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre

Use el `SaveAs` método para guardar un documento con un nuevo nombre. Puede usar este método del <xref:Microsoft.Office.Tools.Word.Document> elemento host en un proyecto de Word de nivel de documento o de un objeto nativo <xref:Microsoft.Office.Interop.Word.Document> en cualquier proyecto de Word. Este método requiere que se especifique el nuevo nombre de archivo, pero otros argumentos son opcionales.

> [!NOTE]
> Si se muestra el cuadro de diálogo **Guardar** como en el <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> controlador de eventos de `ThisDocument` y se establece el parámetro *Cancelar* en **false**, la aplicación podría cerrarse de forma inesperada. Si establece el parámetro *Cancel* en **true**, aparece un mensaje de error que indica que se ha deshabilitado autosave.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Para guardar el documento asociado a una personalización de nivel de documento con un nuevo nombre

1. Llame al `SaveAs` método de la `ThisDocument` clase en el proyecto con una ruta de acceso completa y un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` .

    > [!NOTE]
    > El `SaveAs` método produce una excepción si un directorio de destino no existe o si hay otros problemas para guardar un archivo. Se recomienda usar un `try...catch` bloque alrededor del `SaveAs` método o dentro de un método de llamada.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Para guardar un documento nativo con un nuevo nombre

1. Llame al <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método del <xref:Microsoft.Office.Interop.Word.Document> que desea guardar, mediante una ruta de acceso y un nombre de archivo completos. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.

     En el ejemplo de código siguiente se guarda el documento activo con un nombre nuevo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    > [!NOTE]
    > El <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método produce una excepción si un directorio de destino no existe o si hay otros problemas para guardar un archivo. Se recomienda usar una **instrucción try... bloque catch** alrededor del <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método o dentro de un método de llamada.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Compilar el código

Para este ejemplo de código se necesita lo siguiente:

- Para guardar un documento por su nombre, debe existir un documento denominado *NewDocument.doc* en un directorio denominado *Test* en la unidad C.

- Para guardar un documento con un nuevo nombre, debe existir un directorio denominado *Test* en la unidad C.

## <a name="see-also"></a>Vea también

- [Cómo: cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Cómo: abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elemento host de documento](../vsto/document-host-item.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
