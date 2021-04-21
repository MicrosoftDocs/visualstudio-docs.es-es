---
title: 'Cómo: Abrir documentos existentes mediante programación'
description: Aprenda a usar el método Open para abrir un documento de Microsoft Word existente especificado por una ruta de acceso completa y un nombre de archivo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0153413a357a122b4bb5a1f1cbfb44079f78e128
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827310"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Cómo: Abrir documentos existentes mediante programación
  El método abre el documento Microsoft Office Word especificado por una ruta de acceso <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> completa y un nombre de archivo. Este método devuelve un <xref:Microsoft.Office.Interop.Word.Document> objeto que representa el documento abierto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Para abrir un documento

- Llame al <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> método de la colección y proporcione una ruta de acceso al <xref:Microsoft.Office.Interop.Word.Documents> documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet5":::

## <a name="to-open-a-document-as-read-only"></a>Para abrir un documento como de solo lectura

- Llame al método , proporcione una ruta de acceso al documento y establezca el argumento <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> *ReadOnly* en **True** en la llamada al método.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet6":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento denominado *NewDocument.doc* debe existir en un directorio denominado *Test en* la unidad C.

## <a name="see-also"></a>Consulte también
- [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
