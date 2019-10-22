---
title: Procedimiento Guardar documentos de Visio mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85a45da13594a6f204e91f93ddcee64acb29c493
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419390"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Procedimiento Guardar documentos de Visio mediante programación
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

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre
 Use el método `Microsoft.Office.Interop.Visio.Document.SaveAs` para guardar un nuevo documento, o un documento que tenga un nombre nuevo. Este método requiere que especifique el nombre del archivo nuevo.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Para guardar el documento de Visio activo con un nombre nuevo

- Llame al método `Microsoft.Office.Interop.Visio.Document.SaveAs` del `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.

     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Guardar un documento con un nuevo nombre y argumentos especificados
 Use el método `Microsoft.Office.Interop.Visio.Document.SaveAsEx` para guardar un documento con un nuevo nombre y especifique cualquier argumento correspondiente para aplicar al documento.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Para guardar un documento con un nuevo nombre y argumentos especificados

- Llame al método `Microsoft.Office.Interop.Visio.Document.SaveAsEx` del `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se generará una excepción.

     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre, se marca el documento como de solo lectura y se muestra el documento en la lista de documentos usados más recientemente. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Para guardar un documento que tiene un nuevo nombre, un directorio denominado `Test` debe estar ubicado en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)
