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
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e89c2f986ffc71892682b9fc8ab60b8810850c2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Cómo: Ocultar controles en hojas de cálculo al imprimir
  Al imprimir un documento de Microsoft Office Excel que contiene controles de formularios Windows Forms, los controles son visibles en la hoja de cálculo. Puede ocultar los controles al imprimir una hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si oculta controles que muestran datos, como un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, los datos en el control no estará visibles en la hoja de cálculo.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar los controles cuando una hoja de cálculo se imprime  
  
1.  Crear o abrir un proyecto de Excel en Visual Studio y compruebe que **Sheet1** está visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.Button> el control a una celda en `Sheet1`.  
  
3.  En el **propiedades** ventana, establezca el <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propiedad **False**.  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: agregar controles a documentos de Office de Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  