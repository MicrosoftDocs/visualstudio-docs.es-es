---
title: 'Cómo: abrir documentos existentes mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eba4d110b06147db384a4d7aafe01c7d9f272ba3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519904"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Cómo: abrir documentos existentes mediante programación
  El <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre el documento de Word Microsoft Office existente especificado por una ruta de acceso completa y un nombre de archivo. Este método devuelve un <xref:Microsoft.Office.Interop.Word.Document> que representa el documento abierto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir un documento

- Llame al <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método de la <xref:Microsoft.Office.Interop.Word.Documents> colección y proporcione una ruta de acceso al documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Para abrir un documento como de solo lectura

- Llame al <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, proporcione una ruta de acceso al documento y establezca el argumento *ReadOnly* en **true** en la llamada al método.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento denominado *NewDocument.doc* debe existir en un directorio denominado *Test* en la unidad C.

## <a name="see-also"></a>Vea también
- [Cómo: crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
