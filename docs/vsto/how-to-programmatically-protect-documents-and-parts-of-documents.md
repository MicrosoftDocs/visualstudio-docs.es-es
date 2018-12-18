---
title: 'Cómo: proteger documentos y partes de documentos mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9acef141944b106a9bace38fef8ede7041bfecc5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673885"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Cómo: proteger documentos y partes de documentos mediante programación
  Puede agregar protección a documentos de Microsoft Office Word para impedir que los usuarios realicen cualquier modificación en el documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 También puede marcar determinadas áreas del documento como excepciones para que los usuarios especificados pueden modificar solo dichas áreas del documento. Por ejemplo, puede que desee proteger todo el documento excepto un marcador determinado. Opcionalmente, puede agregar una contraseña para que los usuarios no puedan quitar la protección del documento, a menos que conozcan la contraseña.  
  
> [!NOTE]  
>  El ejemplo siguiente no utiliza protección con contraseña; sin embargo, es recomendable considerar el uso de una contraseña al agregar protección al documento. Para obtener más información, vea el ejemplo de Document Protector en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 También puede usar los controles de contenido para proteger elementos de documentos. Para obtener más información, consulte [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Proteger un documento que forma parte de una personalización de nivel de documento  
  
### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Para proteger un documento que forma parte de una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> de la clase `ThisDocument` en su proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Para excluir un control de marcador de la protección de documento  
  
1.  Proteja todo el documento mediante el método <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Excluya `Bookmark1` de la protección del documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compile-the-code"></a>Compilar el código  
 Para usar estos ejemplos de código, ejecútelos desde la clase `ThisDocument` del proyecto. Estos ejemplos de código suponen que dispone de un control <xref:Microsoft.Office.Tools.Word.Bookmark> existente denominado `Bookmark1` en el documento en el que aparece este código.  
  
## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Proteger un documento mediante un complemento de VSTO  
  
### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Para proteger un documento mediante un complemento de VSTO de nivel de aplicación  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> del <xref:Microsoft.Office.Interop.Word.Document> que quiere proteger.  
  
     El siguiente ejemplo de código protege el documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Cómo: agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  