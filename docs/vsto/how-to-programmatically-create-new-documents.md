---
title: "Cómo: crear nuevos documentos mediante programación | Documentos de Microsoft"
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
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1935b7657e7aad612b855ecd4e9c1c8e222c952
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-documents"></a>Cómo: Crear nuevos documentos mediante programación
  Al crear un documento mediante programación, el nuevo documento es un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo. Este objeto no tiene los eventos y capacidades de enlace de datos adicionales de un elemento host <xref:Microsoft.Office.Tools.Word.Document>. Para obtener más información, consulta [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Al desarrollar un proyecto de nivel de documento, no se pueden agregar elementos host <xref:Microsoft.Office.Tools.Word.Document> al proyecto mediante programación. En un proyecto de complemento de VSTO, puede convertir cualquier objeto <xref:Microsoft.Office.Interop.Word.Document> en un elemento host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución. Para obtener más información, consulta [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-document-based-on-the-normal-template"></a>Para crear un documento nuevo basado en la plantilla Normal  
  
-   Use el método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Documents> para crear un nuevo documento basado en la plantilla Normal. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="using-custom-templates"></a>Usar plantillas personalizadas  
 El <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> método tiene una función opcional *plantilla* argumento para crear un nuevo documento basado en una plantilla distinta de la plantilla Normal. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.  
  
#### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Para crear un documento nuevo basado en una plantilla personalizada  
  
-   Llame al método <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la colección <xref:Microsoft.Office.Interop.Word.Documents> y especifique la ruta de acceso a la plantilla. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  