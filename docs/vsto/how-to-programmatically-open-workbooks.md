---
title: 'Cómo: Abrir libros mediante programación'
description: Obtenga información sobre cómo puede Visual Studio para abrir un libro de Microsoft Excel mediante programación o trabajar con un libro existente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824788"
---
# <a name="how-to-programmatically-open-workbooks"></a>Cómo: Abrir libros mediante programación
  La colección de Microsoft Office Excel permite trabajar con todos los libros abiertos <xref:Microsoft.Office.Interop.Excel.Workbooks> y abrir libros.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Para abrir un libro existente

1. Use el <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método de la colección y pase la ruta de acceso al <xref:Microsoft.Office.Interop.Excel.Workbooks> libro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un libro denominado `YourWorkbook.xls` debe existir en un directorio denominado en la unidad `Test` C.

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Abrir archivos de texto como libros mediante programación](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
