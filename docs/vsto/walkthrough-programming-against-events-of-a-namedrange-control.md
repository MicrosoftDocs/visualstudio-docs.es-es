---
title: 'Tutorial: programar contra eventos de un control NamedRange'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e5ce12e2de8274afd2c27d4ece36529563a6386
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584942"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Tutorial: programar contra eventos de un control NamedRange
  En este tutorial se muestra cómo agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo de Excel Microsoft Office y programar con sus eventos mediante las herramientas de desarrollo de Office en Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo.

- Programe contra <xref:Microsoft.Office.Tools.Excel.NamedRange> eventos de control.

- Pruebe el proyecto.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Crear el proyecto
 En este paso, creará un proyecto de libro de Excel con Visual Studio.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mis eventos de rango con**nombre. Asegúrese de que **la opción crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **mis eventos de rango con nombre** a **Explorador de soluciones**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Agregar texto y rangos con nombre a la hoja de cálculo
 Dado que los controles host son objetos de Office extendidos, puede agregarlos al documento de la misma manera que agregaría el objeto nativo. Por ejemplo, puede Agregar un control de Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo; para ello, abra el menú **Insertar** , seleccione **nombre**y elija **definir**. También puede Agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control arrastrándolo desde el **cuadro de herramientas** hasta la hoja de cálculo.

 En este paso, agregará dos controles de rango con nombre a la hoja de cálculo mediante el **cuadro de herramientas**y, a continuación, agregará texto a la hoja de cálculo.

### <a name="to-add-a-range-to-your-worksheet"></a>Para agregar un intervalo a la hoja de cálculo

1. Compruebe que el libro *mis nombres Events.xlsx* libro está abierto en el diseñador de Visual Studio, con la `Sheet1` muestra.

2. En la pestaña **controles de Excel** del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control hasta la celda **a1** de `Sheet1` .

     Aparece el cuadro de diálogo **Agregar control NamedRange** .

3. Compruebe que aparezca **$A $1** en el cuadro de texto editable y que la celda **a1** esté seleccionada. Si no es así, haga clic en la celda **a1** para seleccionarla.

4. Haga clic en **OK**.

     La celda **a1** se convierte en un intervalo denominado `namedRange1` . No hay ninguna indicación visible en la hoja de cálculo, pero `namedRange1` aparece en el cuadro **nombre** (situado justo encima de la hoja de cálculo en el lado izquierdo) cuando se selecciona la celda **a1** .

5. Agregue otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda **B3**.

6. Compruebe que aparezca **$B $3** en el cuadro de texto editable y que la celda **B3** esté seleccionada. Si no es así, haga clic en la celda **B3** para seleccionarla.

7. Haga clic en **OK**.

     La celda **B3** se convierte en un rango denominado `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Para agregar texto a la hoja de cálculo

1. En la celda **a1**, escriba el texto siguiente:

    **Este es un ejemplo de un control NamedRange.**

2. En la celda **a3** (a la izquierda de `namedRange2` ), escriba el texto siguiente:

    **Ceso**

   En las siguientes secciones, escribirá código que inserta texto en `namedRange2` y modifica las propiedades del `namedRange2` control en respuesta a los <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventos, y <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> de `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Agregar código para responder al evento BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Para insertar texto en NamedRange2 basado en el evento BeforeDoubleClick

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1. VB** o **Sheet1.CS** y seleccione **Ver código**.

2. Agregue código para que el `namedRange1_BeforeDoubleClick` controlador de eventos tenga el aspecto siguiente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. En C#, debe agregar controladores de eventos para el rango con nombre, tal y como se muestra en el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento siguiente. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Agregar código para responder al evento de cambio

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Para insertar texto en namedRange2 basado en el evento de cambio

1. Agregue código para que el `NamedRange1_Change` controlador de eventos tenga el aspecto siguiente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Dado que al hacer doble clic en una celda de un intervalo de Excel entra en el modo de edición, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> se produce un evento cuando la selección se mueve fuera del intervalo aunque no se produzcan cambios en el texto.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Agregar código para responder al evento SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Para insertar texto en namedRange2 basado en el evento SelectionChange

1. Agregue código para que el controlador de eventos **NamedRange1_SelectionChange** tenga el aspecto siguiente:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Dado que al hacer doble clic en una celda de un intervalo de Excel, la selección se mueve al intervalo, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> se produce un evento antes de que <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> se produzca el evento.

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para comprobar que el texto que describe los eventos de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control se inserta en otro rango con nombre cuando se generan los eventos.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Coloque el cursor en `namedRange1` y compruebe que se ha insertado el texto relacionado con el <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento y que se ha insertado un Comentario en la hoja de cálculo.

3. Haga doble clic dentro `namedRange1` de y compruebe que el texto relativo <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> a los eventos se inserta con texto en cursiva rojo en `namedRange2` .

4. Haga clic fuera de `namedRange1` y observe que el evento de cambio se produce al salir del modo de edición, aunque no se haya realizado ningún cambio en el texto.

5. Cambiar el texto dentro de `namedRange1` .

6. Haga clic fuera de `namedRange1` y compruebe que el texto relativo al <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento se inserte con texto azul en `namedRange2` .

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos de la programación en los eventos de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Esta es una tarea que podría aparecer a continuación:

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vea también
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
