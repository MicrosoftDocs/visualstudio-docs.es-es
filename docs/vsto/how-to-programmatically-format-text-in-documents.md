---
title: Procedimiento Dar formato al texto mediante programación en documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66ca84d2246a3335aa3a1bbc0900ca6f48f59f01
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630696"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Procedimiento Dar formato al texto mediante programación en documentos
  Puede utilizar el objeto <xref:Microsoft.Office.Interop.Word.Range> para dar formato al texto de un documento de Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 En el siguiente ejemplo se selecciona el primer párrafo del documento y se cambia el tamaño de la fuente, el nombre de la fuente y la alineación. A continuación, se selecciona el intervalo y se muestra un cuadro de mensaje para hacer una pausa antes de ejecutar la siguiente sección de código. La sección siguiente llama al método Undo del <xref:Microsoft.Office.Tools.Word.Document> elemento host (para una personalización de nivel de documento) o la <xref:Microsoft.Office.Interop.Word.Document> clase (para un complemento de VSTO) tres veces. Aplica el estilo Sangría normal y muestra un cuadro de mensaje para pausar el código. A continuación, el código llama una vez al método <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> y muestra un cuadro de mensaje.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-format-text-using-a-document-level-customization"></a>Para dar formato a un texto mediante una personalización de nivel de documento

1.  El siguiente ejemplo se puede usar en una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Ejemplo para complemento de VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Para dar formato al texto mediante un complemento de VSTO

1.  El siguiente ejemplo se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Vea también
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
