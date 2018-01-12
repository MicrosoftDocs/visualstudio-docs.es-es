---
title: "Cómo: ocultar controles en hojas de cálculo al imprimir | Documentos de Microsoft"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32a967371cb247139285d5db5d3cf88a2a7cc8f9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Cómo: Ocultar controles en hojas de cálculo al imprimir
  Al imprimir un documento de Microsoft Office Excel que contiene controles de formularios Windows Forms, los controles son visibles en la hoja de cálculo. Puede ocultar los controles al imprimir una hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si oculta controles que muestran datos, como un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, los datos en el control no estará visibles en la hoja de cálculo.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar los controles cuando una hoja de cálculo se imprime  
  
1.  Crear o abrir un proyecto de Excel en Visual Studio y compruebe que **Sheet1** está visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.Button> el control a una celda en `Sheet1`.  
  
3.  En el **propiedades** ventana, establezca el <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propiedad **False**.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: agregar controles a documentos de Office de Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  