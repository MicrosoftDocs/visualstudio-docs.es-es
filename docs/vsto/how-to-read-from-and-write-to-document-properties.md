---
title: 'Cómo: leer y escribir en Propiedades de un documento | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f420968461b8f4d11416abe85521ed002cf11ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Cómo: Leer y escribir en propiedades de un documento
  Puede almacenar propiedades de documento junto con un documento. Las aplicaciones de Office proporcionan una serie de propiedades integradas, como author, title y subject. En este tema se muestra cómo establecer las propiedades de documento en Microsoft Office Excel y Microsoft Office Word.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [cómo obtener acceso a y manipular propiedades personalizadas del documento de Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>Establecer las propiedades de un documento en Excel  
 Para trabajar con las propiedades integradas de Excel, use las siguientes propiedades:  
  
-   En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> de la clase `ThisWorkbook` .  
  
-   En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> .  
  
 Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Revision Number** en un proyecto de nivel de documento.  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>Para cambiar la propiedad Revision Number en Excel  
  
1.  Asigne las propiedades integradas del documento a una variable.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Incremente la propiedad `Revision Number` en uno.  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>Establecer las propiedades de un documento en Word  
 Para trabajar con las propiedades integradas de Word, use las siguientes propiedades:  
  
-   En un proyecto de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> de la clase `ThisDocument` .  
  
-   En un proyecto de complemento de VSTO, use la propiedad <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el siguiente ejemplo de código se muestra cómo cambiar la propiedad integrada **Subject** en un proyecto de nivel de documento.  
  
#### <a name="to-change-the-subject-property"></a>Para cambiar la propiedad Subject  
  
1.  Asigne las propiedades integradas del documento a una variable.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Cambie la propiedad `Subject` a «Whitepaper».  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Programación sólida  
 En los ejemplos se supone que ha escrito el código de la clase `ThisWorkbook` en un proyecto de nivel de documento para Excel y la clase `ThisDocument` en un proyecto de nivel de documento para Word.  
  
 Aunque trabaje con Word y Excel y sus objetos, Microsoft Office proporciona una lista de propiedades de documento integradas. Si se intenta tener acceso a una propiedad sin definir, se produce una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programación de personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Cómo: Crear y modificar propiedades personalizadas de documentos](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  