---
title: "Cómo: crear y modificar propiedades de documento personalizadas | Documentos de Microsoft"
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
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5d081beb3422126f6ccf7484cb08e7fa43da8874
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Cómo: Crear y modificar propiedades personalizadas para documentos
  Las aplicaciones de Microsoft Office enumeradas anteriormente proporcionan propiedades integradas que se almacenan con los documentos. Además, puede crear y modificar propiedades de documento personalizadas si hay información adicional que desea almacenar con el documento.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Utilice la propiedad CustomDocumentProperties de un documento para trabajar con propiedades personalizadas. Por ejemplo, en un proyecto de nivel de documento para Microsoft Office Excel, use la propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> de la clase `ThisWorkbook` . En un proyecto de complemento de VSTO para Excel, use la propiedad <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> de un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> . Estas propiedades devuelven un objeto <xref:Microsoft.Office.Core.DocumentProperties> , que es una colección de objetos <xref:Microsoft.Office.Core.DocumentProperty> . Puede usar la propiedad `Item` de la colección para recuperar una propiedad determinada, ya sea por nombre o por índice dentro de la colección.  
  
 En el ejemplo siguiente se muestra cómo agregar una propiedad personalizada en una personalización de nivel de documento para Excel y asignarle un valor.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [cómo obtener acceso a y manipular propiedades personalizadas del documento de Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Si se intenta acceder a la propiedad `Value` para propiedades sin definir, se produce una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programación de personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Cómo: Leer y escribir en propiedades de un documento](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  