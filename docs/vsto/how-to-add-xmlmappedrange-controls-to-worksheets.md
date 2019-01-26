---
title: Procedimiento Agregar controles XMLMappedRange a hojas de cálculo
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e829a3c9a8621856f70fbd8d3a99fb68c6b2a352
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863765"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procedimiento Agregar controles XMLMappedRange a hojas de cálculo
  Al asignar un elemento XML a una celda en Microsoft Office Excel, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control a la hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control no está disponible en el **cuadro de herramientas** o **orígenes de datos** ventana. Además, no se puede crear <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controles mediante programación.  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Para agregar un control XMLMappedRange a una hoja de cálculo  
  
1.  Abra el libro de Excel en el Diseñador de Visual Studio.  
  
2.  Abra la hoja de cálculo en la que desea agregar el control.  
  
3.  En el **Developer** , haga clic **origen**.  
  
    > [!NOTE]  
    >  Si el **Developer** ficha no está visible en la cinta de opciones, debe habilitarla. Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     El **origen XML** aparece el panel de tareas.  
  
4.  En el **origen XML** panel de tareas, haga clic en **mapas XML**.  
  
5.  En el **mapas XML** cuadro de diálogo, haga clic en **agregar**.  
  
     El **origen XML** aparece el cuadro de diálogo.  
  
6.  Seleccione un esquema XML a partir del **origen XML** cuadro de diálogo y haga clic en **abierto**.  
  
     El esquema se agrega a la **mapas XML** cuadro de diálogo.  
  
7.  En el **mapas XML** cuadro de diálogo, haga clic en **Aceptar**.  
  
8.  Arrastre un elemento desde el **origen XML** panel de tareas para una celda en la hoja de cálculo.  
  
     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se crea y agrega al proyecto.  
  
    > [!NOTE]  
    >  Si arrastra un elemento primario de la **origen XML** panel de tareas, un <xref:Microsoft.Office.Tools.Excel.ListObject> se crea el control.  
  
## <a name="see-also"></a>Vea también  
 [XmlMappedRange (control)](../vsto/xmlmappedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
