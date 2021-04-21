---
title: 'Cómo: Mostrar mediante programación una cadena en una celda de hoja de cálculo'
description: Obtenga información sobre cómo puede mostrar mediante programación una cadena en una celda de hoja de cálculo de Microsoft Excel mediante un control NamedRange o un objeto de intervalo nativo de Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825932"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Cómo: Mostrar mediante programación una cadena en una celda de hoja de cálculo
  En este ejemplo se muestra cómo mostrar texto en una celda mediante programación. Para mostrar texto en la celda, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Uso de un control NamedRange
 En este ejemplo se usa <xref:Microsoft.Office.Tools.Excel.NamedRange> un control denominado `message` . El control debe agregarse a una personalización de nivel de documento en tiempo de diseño. El código siguiente debe colocarse en una clase de hoja, no en la `ThisWorkbook` clase .

### <a name="to-display-text-in-a-namedrange-control"></a>Para mostrar texto en un control NamedRange

1. Establezca el valor del <xref:Microsoft.Office.Tools.Excel.NamedRange> control en **Hola mundo**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Usar un intervalo nativo de Excel
 El código siguiente crea un nuevo intervalo mediante programación y, a continuación, le asigna un valor.

### <a name="to-display-text-in-an-excel-range"></a>Para mostrar texto en un intervalo de Excel

1. Recupere el intervalo de la **celda A1** en `Sheet1` y establezca el valor en **Hola mundo**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Consulte también
- [Tutorial: Recopilación de datos mediante windows form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Solución de problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
