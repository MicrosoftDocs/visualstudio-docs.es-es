---
title: Procedimiento Mediante programación contar los caracteres en documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb4bbb124575346c930fa5539801deb3c9981cac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575249"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Procedimiento Mediante programación contar los caracteres en documentos
  El primer carácter de un documento está en la posición de carácter 0, que representa el punto de inserción. La última posición de carácter es igual al número total de caracteres del documento. Puede determinar el número de caracteres de un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la colección <xref:Microsoft.Office.Interop.Word.Characters> .

 Se cuentan todos los caracteres en el documento, incluidos los espacios, las marcas de párrafo y otros caracteres que normalmente están ocultos. Incluso un nuevo documento en blanco devuelve un recuento de caracteres porque contiene una marca de párrafo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Para mostrar el número de caracteres en una personalización de nivel de documento

1. Seleccione todo el documento.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Muestre el número de caracteres del documento en un cuadro de mensaje.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Para mostrar el número de caracteres en un complemento de VSTO

1. Seleccione todo el documento. El siguiente ejemplo selecciona el documento activo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Muestre el número de caracteres del documento en un cuadro de mensaje.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>Vea también
- [Cómo: Recuperar los caracteres inicial y final en los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
