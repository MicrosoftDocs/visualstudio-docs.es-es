---
title: "Cómo: agregar controles XMLMappedRange a hojas de cálculo | Documentos de Microsoft"
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
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 59c82cd16da614229cedd01bccd7a5057246299c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Cómo: Agregar controles XMLMappedRange a hojas de cálculo
  Al asignar un elemento XML a una celda en Microsoft Office Excel, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control a la hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control no está disponible en la **cuadro de herramientas** o **orígenes de datos** ventana. Además, no se puede crear <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controles mediante programación.  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Para agregar un control XMLMappedRange a una hoja de cálculo  
  
1.  Abra el libro de Excel en el Diseñador de Visual Studio.  
  
2.  Abra la hoja de cálculo en la que desea agregar el control.  
  
3.  En el **Developer** , haga clic en **origen**.  
  
    > [!NOTE]  
    >  Si el **Developer** ficha no está visible en la cinta de opciones, debe habilitarla. Para obtener más información, consulta [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     El **origen XML** aparece el panel de tareas.  
  
4.  En el **origen XML** panel de tareas, haga clic en **asignaciones XML**.  
  
5.  En el **asignaciones XML** cuadro de diálogo, haga clic en **agregar**.  
  
     El **origen XML** aparece el cuadro de diálogo.  
  
6.  Seleccione un esquema XML desde el **origen XML** cuadro de diálogo y haga clic en **abiertos**.  
  
     El esquema se agrega a la **asignaciones XML** cuadro de diálogo.  
  
7.  En el **asignaciones XML** cuadro de diálogo, haga clic en **Aceptar**.  
  
8.  Arrastre un elemento desde el **origen XML** panel de tareas hasta una celda en la hoja de cálculo.  
  
     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se crea y se agrega al proyecto.  
  
    > [!NOTE]  
    >  Si se arrastra un elemento primario de la **origen XML** panel de tareas, una <xref:Microsoft.Office.Tools.Excel.ListObject> se crea el control.  
  
## <a name="see-also"></a>Vea también  
 [XmlMappedRange (Control)](../vsto/xmlmappedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  