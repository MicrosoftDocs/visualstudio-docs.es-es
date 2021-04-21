---
title: 'Cómo: Guardar documentos mediante programación'
description: Obtenga información sobre cómo puede Visual Studio guardar un documento mediante programación sin cambiar el nombre del documento o con un nuevo nombre.
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
ms.openlocfilehash: 97f56ce0bd44eac71430a099b4fda9a7eddc7958
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829013"
---
# <a name="how-to-programmatically-save-documents"></a>Cómo: Guardar documentos mediante programación

Hay varias maneras de guardar documentos Microsoft Office Word. Puede guardar un documento sin cambiar el nombre del documento o puede guardar un documento con un nuevo nombre.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Guardar un documento sin cambiar el nombre

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Para guardar el documento asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>Para guardar el documento activo

1. Llame al <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método para el documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   Si no está seguro de si el documento que desea guardar es el documento activo, puede hacer referencia a él por su nombre.

### <a name="to-save-a-document-specified-by-name"></a>Para guardar un documento especificado por nombre

1. Use el nombre del documento como argumento de la <xref:Microsoft.Office.Interop.Word.Documents> colección. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre

Use el `SaveAs` método para guardar un documento con un nuevo nombre. Puede usar este método del elemento host en un proyecto de Word de nivel de documento o de <xref:Microsoft.Office.Tools.Word.Document> un objeto nativo en cualquier proyecto de <xref:Microsoft.Office.Interop.Word.Document> Word. Este método requiere que especifique el nuevo nombre de archivo, pero otros argumentos son opcionales.

> [!NOTE]
> Si muestra el cuadro **de diálogo SaveAs** dentro del controlador de eventos de y establece el parámetro Cancel en false, es posible que la aplicación <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> se cierre `ThisDocument`  inesperadamente.  Si establece el parámetro *Cancel* en **true,** aparece un mensaje de error que indica que autoguardado se ha deshabilitado.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Para guardar el documento asociado a una personalización de nivel de documento con un nuevo nombre

1. Llame al método de la clase en el proyecto mediante una ruta `SaveAs` de acceso completa y un nombre de `ThisDocument` archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` .

    > [!NOTE]
    > El método produce una excepción si no existe un directorio de destino o si `SaveAs` hay otros problemas al guardar un archivo. Es una buena práctica usar un bloque alrededor `try...catch` del método o dentro de un método de `SaveAs` llamada.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>Para guardar un documento nativo con un nuevo nombre

1. Llame al método del que desea guardar, mediante una ruta de acceso <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> completa y un nombre de <xref:Microsoft.Office.Interop.Word.Document> archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.

     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

    > [!NOTE]
    > El método produce una excepción si no existe un directorio de destino o si <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> hay otros problemas al guardar un archivo. Es un procedimiento recomendado usar una **prueba... bloque catch** alrededor del <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> método o dentro de un método de llamada.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>Compilar el código

Para este ejemplo de código se necesita lo siguiente:

- Para guardar un documento por nombre, debe existir un *documentoNewDocument.doc* en un directorio denominado *Test* en la unidad C.

- Para guardar un documento con un nuevo nombre, debe existir un directorio denominado *Test* en la unidad C.

## <a name="see-also"></a>Consulte también

- [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elemento host de documento](../vsto/document-host-item.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
