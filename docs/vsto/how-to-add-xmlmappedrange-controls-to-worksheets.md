---
title: 'Cómo: agregar controles XMLMappedRange a hojas de cálculo | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fa0e6d6249ea9b7da3fb0ab57640b61fb38e7fe5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
    >  Si el **Developer** ficha no está visible en la cinta de opciones, debe habilitarla. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
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
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  