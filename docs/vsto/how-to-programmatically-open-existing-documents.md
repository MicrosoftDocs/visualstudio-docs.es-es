---
title: Procedimiento Abrir documentos existentes mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 490dda6e5357cd0933c6a8b494cc4373038e5c1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812403"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procedimiento Abrir documentos existentes mediante programación
  El <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre el documento de Microsoft Office Word existente especificado por un nombre de ruta de acceso y nombre completo. Este método devuelve un <xref:Microsoft.Office.Interop.Word.Document> que representa el documento abierto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir un documento

- Llame a la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método de la <xref:Microsoft.Office.Interop.Word.Documents> colección y proporcionar una ruta de acceso al documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Para abrir un documento como de solo lectura

- Llame a la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, proporcione una ruta de acceso al documento y establecer el *ReadOnly* argumento **True** en la llamada al método.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento denominado *NewDocument.doc* debe existir en un directorio denominado *prueba* en la unidad C.

## <a name="see-also"></a>Vea también
- [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
