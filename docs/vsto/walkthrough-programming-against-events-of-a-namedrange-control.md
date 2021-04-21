---
title: 'Tutorial: Programación con eventos de un control NamedRange'
description: Obtenga información sobre cómo agregar un control NamedRange a una hoja de cálculo y un programa de Microsoft Excel con sus eventos mediante las herramientas de desarrollo de Office en Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec1c670867fae277a3c3c8290cd34d0d4be7ddf3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824970"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Tutorial: Programación con eventos de un control NamedRange
  En este tutorial se muestra cómo agregar un control a una hoja de cálculo y un programa de Microsoft Office Excel con sus eventos mediante el uso de herramientas de desarrollo de <xref:Microsoft.Office.Tools.Excel.NamedRange> Office en Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregue un control a <xref:Microsoft.Office.Tools.Excel.NamedRange> una hoja de cálculo.

- Programe con <xref:Microsoft.Office.Tools.Excel.NamedRange> eventos de control.

- Pruebe el proyecto.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creación del proyecto
 En este paso, creará un proyecto de libro de Excel mediante Visual Studio.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **My Named Range Events**. Asegúrese de que **está seleccionada la opción Crear** un documento nuevo. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **proyecto Mis** eventos de intervalo con nombre **a Explorador de soluciones**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Agregar texto e intervalos con nombre a la hoja de cálculo
 Dado que los controles host son objetos extendidos de Office, puede agregarlos al documento de la misma manera que agregaría el objeto nativo. Por ejemplo, puede agregar un control de Excel a una hoja de cálculo abriendo el menú Insertar, apuntando a Nombre y <xref:Microsoft.Office.Tools.Excel.NamedRange> **seleccionando Definir**.   También puede agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control arrastrándolo desde el Cuadro **de herramientas** a la hoja de cálculo.

 En este paso, agregará dos controles de rango con nombre a la hoja de cálculo mediante el Cuadro de herramientas y, a continuación, agregará texto a la hoja de cálculo.

### <a name="to-add-a-range-to-your-worksheet"></a>Para agregar un intervalo a la hoja de cálculo

1. Compruebe que el *libro My Named Range Events.xlsx* (Mi intervalo con nombre) está abierto en Visual Studio diseñador, con la vista `Sheet1` mostrada.

2. En la **pestaña Controles de Excel** del Cuadro de herramientas, arrastre un control a la celda <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** en `Sheet1` .

     Aparece **el cuadro de diálogo Agregar control NamedRange.**

3. Compruebe que **$A$1** aparece en el cuadro de texto editable y que la **celda A1** está seleccionada. Si no es así, haga clic en la **celda A1** para seleccionarla.

4. Haga clic en **OK**.

     La **celda A1** se convierte en un intervalo denominado `namedRange1` . No hay ninguna indicación visible en la hoja de cálculo, pero aparece en el cuadro Nombre (situado justo encima de la hoja de cálculo del lado izquierdo) cuando se selecciona `namedRange1` la celda **A1.** 

5. Agregue otro <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda **B3.**

6. Compruebe que **$B$3** aparece en el cuadro de texto editable y que la **celda B3** está seleccionada. Si no es así, haga clic en la **celda B3** para seleccionarla.

7. Haga clic en **OK**.

     La **celda B3** se convierte en un intervalo denominado `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Para agregar texto a la hoja de cálculo

1. En Celda **A1,** escriba el texto siguiente:

    **Este es un ejemplo de un control NamedRange.**

2. En Cell **A3** (a la izquierda de `namedRange2` ), escriba el texto siguiente:

    **Eventos:**

   En las secciones siguientes, escribirá código que inserta texto en y modifica las propiedades del control en respuesta a los eventos `namedRange2` `namedRange2` , y de <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Agregar código para responder al evento BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Para insertar texto en NamedRange2 según el evento BeforeDoubleClick

1. En **Explorador de soluciones**, haga clic con el botón derecho **en Sheet1.vb o** **Sheet1.cs** y seleccione **Ver código.**

2. Agregue código para que `namedRange1_BeforeDoubleClick` el controlador de eventos sea similar al siguiente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. En C#, debe agregar controladores de eventos para el intervalo con nombre, como se muestra en el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento siguiente. Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Agregar código para responder al evento Change

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Para insertar texto en namedRange2 según el evento Change

1. Agregue código para que `NamedRange1_Change` el controlador de eventos sea similar al siguiente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Dado que al hacer doble clic en una celda de un intervalo de Excel entra en modo de edición, se produce un evento cuando la selección se mueve fuera del intervalo incluso si no se ha producido ningún cambio en <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> el texto.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Agregar código para responder al evento SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Para insertar texto en namedRange2 según el evento SelectionChange

1. Agregue código para que **el NamedRange1_SelectionChange** de eventos sea similar al siguiente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Dado que hacer doble clic en una celda de un intervalo de Excel hace que la selección se mueva al intervalo, se produce un evento antes <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> de que se produzca el <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> evento.

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para comprobar que el texto que describe los eventos de un control se inserta en otro intervalo con nombre <xref:Microsoft.Office.Tools.Excel.NamedRange> cuando se genera el evento.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Coloque el cursor en y compruebe que se inserta el texto relacionado con el evento y `namedRange1` que se inserta un comentario en la hoja de <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> cálculo.

3. Haga doble clic dentro de y compruebe que el texto relativo `namedRange1` a los eventos se inserta con texto en <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> cursiva rojo en `namedRange2` .

4. Haga clic fuera de y observe que el evento de cambio se produce al salir del modo de edición aunque no se haya realizado `namedRange1` ningún cambio en el texto.

5. Cambie el texto dentro de `namedRange1` .

6. Haga clic fuera de y compruebe que el texto relacionado `namedRange1` con el evento se inserta con texto azul en <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> `namedRange2` .

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos de la programación con respecto a los eventos de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control . Esta es una tarea que podría ser la siguiente:

- Implementación del proyecto. Para obtener más información, vea [Implementar una solución de Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Consulte también
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
