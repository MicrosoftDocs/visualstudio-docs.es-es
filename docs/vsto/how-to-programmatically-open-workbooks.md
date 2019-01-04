---
title: Procedimiento Abrir libros mediante programación
ms.date: 02/02/2017
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
ms.openlocfilehash: ab91a1e9a89edee013b559f1653c1607e7b8c884
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860954"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedimiento Abrir libros mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Workbooks> colección en Microsoft Office Excel hace posible para trabajar con todos los libros abiertos y abrir los libros.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-open-an-existing-workbook"></a>Para abrir un libro existente  
  
1.  Use la <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método de la <xref:Microsoft.Office.Interop.Excel.Workbooks> colección, pasando la ruta de acceso al libro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un libro denominado `YourWorkbook.xls` debe existir en un directorio denominado `Test` en la unidad C.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: Abrir archivos de texto mediante programación como libros](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)  
