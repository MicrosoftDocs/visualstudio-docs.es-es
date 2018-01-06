---
title: "Cómo: guardar libros mediante programación | Documentos de Microsoft"
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
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d0aa6421893c9d930f917e98fb8aa85b6ceb28d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-workbooks"></a>Cómo: Guardar libros mediante programación
  Existen varias formas de guardar un libro. Puede guardar un libro sin cambiar la ruta de acceso. Si el libro nunca se guardó, debe guardarlo especificando una ruta de acceso. Sin una ruta de acceso explícita, Microsoft Office Excel guarda el archivo en la carpeta actual con el nombre que se especificó cuando se creó. También puede guardar una copia del libro sin modificar el libro abierto en memoria.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>Guardar un libro sin cambiar la ruta de acceso  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> de la clase ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> para guardar el libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>Guardar un libro con una nueva ruta de acceso  
 Puede guardar el libro especificado en una ubicación nueva o con un nombre nuevo, especificando opcionalmente un formato de archivo, una contraseña y un modo de acceso, entre otras cosas.  
  
> [!NOTE]  
>  Desea establecer el <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> propiedad **False** antes de guardar el libro con una nueva ruta de acceso, ya que guardar en algunos formatos requiere interacción. Si se establece esta propiedad en **False** , Excel usa todos los valores predeterminados.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de la clase `ThisWorkbook`. Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> para guardar el libro activo en una nueva ruta de acceso. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>Guardar una copia del libro  
 Puede guardar una copia del libro en un archivo sin modificar el libro abierto en memoria. Esto es útil cuando se desea crear una copia de seguridad sin modificar la ubicación del libro.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> de la clase `ThisWorkbook`. Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> para guardar una copia del libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Si se cancela interactivamente cualquiera de los métodos que guardan o copian el libro se produce un error en tiempo de ejecución en el código. Por ejemplo, si el procedimiento llama el <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> método pero no deshabilita los mensajes de Excel, y el usuario hace clic en **cancelar** cuando se le solicite, Excel genera un error en tiempo de ejecución.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Elemento Host Workbook](../vsto/workbook-host-item.md)   
 [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  