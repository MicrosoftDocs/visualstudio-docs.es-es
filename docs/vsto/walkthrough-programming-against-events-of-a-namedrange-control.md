---
title: 'Tutorial: Programar basándose en eventos de un control NamedRange'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ab9810ba5086d3de8f5d3ad91bc2c62e0d30d349
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675343"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Tutorial: Programar basándose en eventos de un control NamedRange
  Este tutorial muestra cómo agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo de Microsoft Office Excel y programar sus eventos mediante el uso de herramientas de desarrollo de Office en Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo.  
  
-   Programar <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar eventos.  
  
-   Pruebe el proyecto.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Crear el proyecto  
 En este paso, creará un proyecto de libro de Excel con Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mis eventos de intervalo con nombre**. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mis eventos de intervalo con nombre** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Agregar texto y rangos con nombre a la hoja de cálculo  
 Dado que los controles host son objetos de Office extendidos, puede agregarlos a su documento de la misma manera agregaría el objeto nativo. Por ejemplo, puede agregar un Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> control a una hoja de cálculo abriendo el **insertar** menú, seleccione **nombre**y elegir **definir**. También puede agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control arrastrándolo desde la **cuadro de herramientas** en la hoja de cálculo.  
  
 En este paso, agregará dos controles de rango con nombre a la hoja de cálculo mediante la **cuadro de herramientas**y, a continuación, agregue texto a la hoja de cálculo.  
  
### <a name="to-add-a-range-to-your-worksheet"></a>Para agregar un intervalo a la hoja de cálculo  
  
1.  Compruebe que la *Events.xlsx de intervalo denominado My* libro está abierto en el Diseñador de Visual Studio, con `Sheet1` muestra.  
  
2.  Desde el **controles de Excel** ficha del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda **A1** en `Sheet1`.  
  
     El **agregar NamedRange Control** aparece el cuadro de diálogo.  
  
3.  Compruebe que **$A$ 1** aparece en el cuadro de texto editable y esa celda **A1** está seleccionada. Si no es así, haga clic en la celda **A1** para seleccionarlo.  
  
4.  Haga clic en **Aceptar**.  
  
     Celda **A1** se convierte en un rango con nombre `namedRange1`. No hay ninguna indicación visible en la hoja de cálculo, pero `namedRange1` aparece en el **nombre** (situada justo encima de la hoja de cálculo en el lado izquierdo) cuando la celda **A1** está seleccionada.  
  
5.  Agregue otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda **B3**.  
  
6.  Compruebe que **$B$ 3** aparece en el cuadro de texto editable y esa celda **B3** está seleccionada. Si no es así, haga clic en la celda **B3** para seleccionarlo.  
  
7.  Haga clic en **Aceptar**.  
  
     Celda **B3** se convierte en un rango con nombre `namedRange2`.  
  
### <a name="to-add-text-to-your-worksheet"></a>Para agregar texto a la hoja de cálculo  
  
1.  En la celda **A1**, escriba el texto siguiente:  
  
     **Esto es un ejemplo de un control NamedRange.**  
  
2.  En la celda **A3** (a la izquierda del `namedRange2`), escriba el texto siguiente:  
  
     **Eventos:**  
  
 En las secciones siguientes, escribirá código que inserta texto en `namedRange2` y modifica las propiedades de la `namedRange2` control en respuesta a la <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, y <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> eventos de `namedRange1`.  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Agregue código para responder al evento BeforeDoubleClick  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Para insertar texto en NamedRange2 basado en el evento BeforeDoubleClick  
  
1.  En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs** y seleccione **ver código**.  
  
2.  Agregue código para que el `namedRange1_BeforeDoubleClick` controlador de eventos es similar al siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  En C#, debe agregar controladores de eventos para el rango con nombre, como se muestra en el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento siguiente. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>Agregue código para responder al evento de cambio  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Para insertar texto en namedRange2 basado en el evento de cambio  
  
1.  Agregue código para que el `NamedRange1_Change` controlador de eventos es similar al siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Dado que haga doble clic en una celda de un rango de Excel entra en modo de edición, un <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento se produce cuando la selección se mueve fuera del intervalo, incluso si se ha producido ningún cambio en el texto.  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Agregue código para responder al evento SelectionChange  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Para insertar texto en namedRange2 basado en SelectionChange (evento)  
  
1.  Agregue código para que el **NamedRange1_SelectionChange** controlador de eventos es similar al siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Dado que haga doble clic en una celda de un rango de Excel hace que la selección se mueva en el intervalo, un <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento tiene lugar antes de la <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> se produce el evento.  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para comprobar ese texto que describe los eventos de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control se inserta en otro rango con nombre cuando se producen los eventos.  
  
### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Coloque el cursor en `namedRange1`y compruebe que el texto sobre el <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> se insertan eventos y que se inserta un comentario en la hoja de cálculo.  
  
3.  Haga doble clic dentro de `namedRange1`y compruebe que el texto sobre <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> eventos se inserta con texto rojo en cursiva en `namedRange2`.  
  
4.  Haga clic fuera de `namedRange1` y tenga en cuenta que el evento de cambio se produce al salir de modo de edición, aunque se haya realizado ningún cambio en el texto.  
  
5.  Cambiar el texto dentro de `namedRange1`.  
  
6.  Haga clic fuera de `namedRange1`y compruebe que el texto sobre <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventos se insertan con texto azul en `namedRange2`.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Este tutorial muestran los aspectos básicos de programación en los eventos de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Aquí es una tarea que podría realizar las siguiente:  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  