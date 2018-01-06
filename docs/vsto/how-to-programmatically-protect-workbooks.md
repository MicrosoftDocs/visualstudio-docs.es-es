---
title: "Cómo: proteger libros mediante programación | Documentos de Microsoft"
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
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5c383c95d37894aaa49a4a42d2b9a17b9a193f41
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-protect-workbooks"></a>Cómo: Proteger libros mediante programación
  Puede proteger un libro de Microsoft Office Excel para que los usuarios no pueden agregar o eliminar hojas de cálculo y también puede desproteger el libro mediante programación. Si lo desea, puede especificar una contraseña, indicar si desea que la estructura protegida (por lo que los usuarios no pueden mover las hojas) y que indique si desea que estén protegidas las ventanas del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Proteger un libro no impedir que los usuarios editen celdas. Para proteger los datos, debe proteger las hojas de cálculo. Para obtener más información, consulte [Cómo: proteger hojas mediante programación](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Los ejemplos de código siguiente usan una variable para contener una contraseña obtenida del usuario.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Proteger un libro que forma parte de una personalización de nivel de documento  
  
#### <a name="to-protect-a-workbook"></a>Para proteger un libro  
  
1.  Llame a la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método del libro e incluya una contraseña. Para usar el ejemplo de código siguiente, ejecútelo la `ThisWorkbook` (clase), no en una clase sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Para desproteger un libro  
  
1.  Llame a la <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> método, pasando una contraseña si es necesario. Para usar el ejemplo de código siguiente, ejecútelo la `ThisWorkbook` (clase), no en una clase sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Proteger un libro mediante un complemento de nivel de aplicación  
  
#### <a name="to-protect-a-workbook"></a>Para proteger un libro  
  
1.  Llame a la <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> método del libro e incluya una contraseña. Este ejemplo de código usa el libro activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Para desproteger un libro  
  
1.  Llame a la <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> método del libro activo, pasando una contraseña si es necesario. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: proteger hojas de cálculo de mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Cómo: ocultar hojas de cálculo de mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  