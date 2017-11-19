---
title: "Cómo: abrir libros mediante programación | Documentos de Microsoft"
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7768aec2684e95c0201c88713e4a342737ce3cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-open-workbooks"></a>Cómo: Abrir libros mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Workbooks> colección de Microsoft Office Excel hace posible que se va a trabajar con todos los libros abiertos como abrir libros.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Para abrir un libro existente  
  
1.  Use la <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método de la <xref:Microsoft.Office.Interop.Excel.Workbooks> colección, pasando la ruta de acceso al libro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un libro denominado `YourWorkbook.xls` debe existir en un directorio denominado `Test` en la unidad C.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: abrir archivos de texto como libros de mediante programación](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Cómo: crear nuevos libros de mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  