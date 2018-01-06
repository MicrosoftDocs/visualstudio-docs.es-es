---
title: "Cómo: agregar mediante programación los encabezados y pies de página a documentos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b0f2651fc4bfedab3c7308c7fa7e8cef604666f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Cómo: Agregar encabezados y pies de página a documentos mediante programación
  Puede agregar texto a los encabezados y pies de página del documento mediante las propiedades <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> y <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de la <xref:Microsoft.Office.Interop.Word.Section>. Cada sección de un documento contiene tres encabezados y pies de página:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Los procedimientos son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>personalizaciones de nivel de documento  
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisDocument` del proyecto.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Para agregar texto a los pies de página en el documento  
  
1.  En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento  
  
1.  En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO Add-ins  
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisAddIn` del proyecto.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Para agregar texto a los pies de página de un documento  
  
1.  En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página. Este ejemplo de código usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento  
  
1.  En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado. Este ejemplo de código usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)   
 [Cómo: ampliar intervalos en documentos de mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   