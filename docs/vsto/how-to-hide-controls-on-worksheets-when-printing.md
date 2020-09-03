---
title: 'Cómo: ocultar controles en hojas de cálculo al imprimir'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 336723f60a2cd90dc63db24e981dd06e0388cb9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544812"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Cómo: ocultar controles en hojas de cálculo al imprimir
  Al imprimir un Microsoft Office documento de Excel que contiene Windows Forms controles, los controles están visibles en la hoja de cálculo impresa. Puede ocultar los controles al imprimir una hoja de cálculo.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Si oculta controles que muestran datos, como un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , los datos del control no estarán visibles en la hoja de cálculo impresa.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar controles cuando se imprime una hoja de cálculo

1. Cree o abra un proyecto de Excel en Visual Studio y compruebe que **Sheet1** está visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.Button> control a una celda de `Sheet1` .

3. En la ventana **propiedades** , establezca la <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propiedad en **false**.

## <a name="see-also"></a>Consulte también
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)
