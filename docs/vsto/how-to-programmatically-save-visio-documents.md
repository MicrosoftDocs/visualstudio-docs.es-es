---
title: 'Cómo: Guardar documentos de Visio mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio guardar mediante programación documentos existentes de Microsoft Visio y nuevos documentos que aún no se han guardado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 340d813a19c0c0dc5c347d3cfe4c7b29ff1bd049
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829000"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Cómo: Guardar documentos de Visio mediante programación
  Hay varias formas de guardar documentos de Microsoft Office Visio:

- Guardar cambios en un documento existente.

- Guardar un documento nuevo, o guardar un documento con un nuevo nombre.

- Guardar un documento con argumentos especificados.

  Para obtener más información, vea la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) y [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .

## <a name="save-an-existing-document"></a>Guardar un documento existente

### <a name="to-save-a-document"></a>Para guardar un documento

- Llame al método `Microsoft.Office.Interop.Visio.Document.Save` de la clase `Microsoft.Office.Tools.Visio.Document` de un documento que ya se ha guardado.

     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

    > [!NOTE]
    > El método `Microsoft.Office.Interop.Visio.Document.Save` produce una excepción si todavía no se ha guardado un nuevo documento de Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre
 Use el método `Microsoft.Office.Interop.Visio.Document.SaveAs` para guardar un nuevo documento, o un documento que tenga un nombre nuevo. Este método requiere que especifique el nombre del archivo nuevo.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Para guardar el documento de Visio activo con un nombre nuevo

- Llame al método `Microsoft.Office.Interop.Visio.Document.SaveAs` del `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.

     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Guardar un documento con un nuevo nombre y argumentos especificados
 Use el método `Microsoft.Office.Interop.Visio.Document.SaveAsEx` para guardar un documento con un nuevo nombre y especifique cualquier argumento correspondiente para aplicar al documento.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Para guardar un documento con un nuevo nombre y argumentos especificados

- Llame al método `Microsoft.Office.Interop.Visio.Document.SaveAsEx` del `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se generará una excepción.

     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre, se marca el documento como de solo lectura y se muestra el documento en la lista de documentos usados más recientemente. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Para guardar un documento con un nuevo nombre, un directorio denominado debe encontrarse en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta Documentos `Test` (para Windows  Vista). 

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)
