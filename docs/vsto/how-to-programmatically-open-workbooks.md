---
title: 'Cómo: abrir libros mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd8f6786bd2f7b54ce6b50f2493ebd5d45bba51e
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257363"
---
# <a name="how-to-programmatically-open-workbooks"></a>Cómo: abrir libros mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Workbooks> colección en Microsoft Office Excel hace posible para trabajar con todos los libros abiertos y abrir los libros.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-open-an-existing-workbook"></a>Para abrir un libro existente  
  
1.  Use la <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método de la <xref:Microsoft.Office.Interop.Excel.Workbooks> colección, pasando la ruta de acceso al libro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un libro denominado `YourWorkbook.xls` debe existir en un directorio denominado `Test` en la unidad C.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: abrir archivos de texto como libros mediante programación](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)  
  
  