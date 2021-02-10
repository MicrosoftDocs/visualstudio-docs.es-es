---
title: 'Cómo: agregar controles XmlMappedRange (a hojas de cálculo'
description: Sepa que al asignar un elemento XML a una celda en Microsoft Office Excel, Visual Studio agrega automáticamente un control XmlMappedRange (a la hoja de cálculo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 065a904047630d15a8e9ed167a6a4a2764858387
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970327"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Cómo: agregar controles XmlMappedRange (a hojas de cálculo
  Al asignar un elemento XML a una celda en Microsoft Office Excel, Visual Studio agrega automáticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control a la hoja de cálculo.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> El <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control no está disponible en el **cuadro de herramientas** o en la ventana **orígenes de datos** . Además, no puede crear <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controles mediante programación.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Para agregar un control XmlMappedRange (a una hoja de cálculo

1. Abra el libro de Excel en el diseñador de Visual Studio.

2. Abra la hoja de cálculo en la que desea agregar el control.

3. En la pestaña **desarrollador** , haga clic en **origen**.

    > [!NOTE]
    > Si la pestaña **desarrollador** no está visible en la cinta de opciones, debe habilitarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Aparece el panel de tareas **origen XML** .

4. En el panel de tareas **origen XML** , haga clic en **asignaciones XML**.

5. En el cuadro de diálogo **asignaciones XML** , haga clic en **Agregar**.

     Aparecerá el cuadro de diálogo **origen XML** .

6. Seleccione un esquema XML en el cuadro de diálogo **origen XML** y haga clic en **abrir**.

     El esquema se agrega al cuadro de diálogo **asignaciones XML** .

7. En el cuadro de diálogo **asignaciones XML** , haga clic en **Aceptar**.

8. Arrastre un elemento desde el panel de tareas **origen XML** hasta una celda de la hoja de cálculo.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Se crea y se agrega al proyecto.

    > [!NOTE]
    > Si arrastra un elemento primario desde el panel de tareas **origen XML** , <xref:Microsoft.Office.Tools.Excel.ListObject> se crea un control.

## <a name="see-also"></a>Vea también
- [Control XmlMappedRange (](../vsto/xmlmappedrange-control.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
