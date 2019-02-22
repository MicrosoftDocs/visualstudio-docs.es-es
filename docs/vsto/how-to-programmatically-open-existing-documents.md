---
title: Filtrar Abrir documentos existentes mediante programación
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
ms.openlocfilehash: 3e31e5307acb8dadd627cc0a7a0c65572c7ab219
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56653988"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procedimiento Abrir documentos existentes mediante programación
  El <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método abre el documento de Microsoft Office Word existente especificado por un nombre de ruta de acceso y nombre completo. Este método devuelve un <xref:Microsoft.Office.Interop.Word.Document> que representa el documento abierto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir un documento

-   Llame a la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método de la <xref:Microsoft.Office.Interop.Word.Documents> colección y proporcionar una ruta de acceso al documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Para abrir un documento como de solo lectura

-   Llame a la <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método, proporcione una ruta de acceso al documento y establecer el *ReadOnly* argumento **True** en la llamada al método.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

-   Un documento denominado *NewDocument.doc* debe existir en un directorio denominado *prueba* en la unidad C.

## <a name="see-also"></a>Vea también
- [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
