---
title: Procedimiento Ocultar controles en hojas de cálculo al imprimir
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 322c314a768545996f343526367de44c667ce89b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646804"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Procedimiento Ocultar controles en hojas de cálculo al imprimir
  Al imprimir un documento de Microsoft Office Excel que contiene controles de formularios Windows Forms, los controles están visibles en la hoja de cálculo. Puede ocultar los controles al imprimir una hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si ocultar los controles que muestran datos, como un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, los datos en el control no estará visibles en la hoja de cálculo.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar los controles cuando una hoja de cálculo se imprime  
  
1.  Crear o abrir un proyecto de Excel en Visual Studio y compruebe que **Sheet1** está visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.Button> el control a una celda en `Sheet1`.  
  
3.  En el **propiedades** ventana, establezca el <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propiedad **False**.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Controles de Windows Forms en información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  