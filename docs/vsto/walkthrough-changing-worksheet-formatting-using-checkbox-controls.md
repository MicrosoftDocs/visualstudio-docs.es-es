---
title: Cambiar el formato de la hoja de cálculo mediante controles CheckBox
description: Obtenga información sobre cómo puede usar las herramientas de desarrollo de Office en Visual Studio para crear y agregar código al proyecto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28b9f000c2e8517304387e2b203dfa7888b33d64
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527217"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Tutorial: cambiar el formato de una hoja de cálculo mediante controles CheckBox
  En este tutorial se muestran los aspectos básicos del uso de las casillas en una Microsoft Office hoja de cálculo de Excel para cambiar el formato. Usará las herramientas de desarrollo de Office en Visual Studio para crear y agregar código al proyecto. Para ver el resultado como un ejemplo completado, vea el ejemplo de controles de Excel en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar texto y controles a una hoja de cálculo.

- Dar formato al texto cuando se selecciona una opción.

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

1. Cree un proyecto de libro de Excel con el nombre **mi formato de Excel**. Asegúrese de que **la opción crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto de **formato My Excel** a **Explorador de soluciones**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Agregar texto y controles a la hoja de cálculo
 Para este tutorial, necesitará tres <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controles y texto en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control.

### <a name="to-add-three-check-boxes"></a>Para agregar tres casillas

1. Compruebe que el libro está abierto en el diseñador de Visual Studio y que `Sheet1` está abierto.

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> control hacia o cerca de la celda **B2** en **Sheet1**.

3. En el menú **Ver** , seleccione ventana **propiedades** .

4. Asegúrese de que **Checkbox1** esté visible en el cuadro de lista nombre de objeto de la ventana **propiedades** y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyBoldFont**|
    |**Texto**|**Negrita**|

5. Arrastre una segunda casilla a la celda **B4** o cerca de ella y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyItalicFont**|
    |**Texto**|**Cursiva**|

6. Arrastre una tercera casilla en o cerca de la celda **B6** y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyUnderlineFont**|
    |**Texto**|**Subrayado**|

7. Active los tres controles de casilla mientras mantiene presionada la tecla **Ctrl** .

8. En el grupo organizar de la pestaña formato de Excel, haga clic en **alinear** y, a continuación, haga clic en **alinear** a la izquierda.

     Los tres controles de casilla están alineados en el lado izquierdo, en la posición del primer control seleccionado.

     A continuación, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la hoja de cálculo.

    > [!NOTE]
    > También puede Agregar el <xref:Microsoft.Office.Tools.Excel.NamedRange> control escribiendo **textFont** en el cuadro **nombre** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Para agregar texto a un control NamedRange

1. En la pestaña **controles de Excel** del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control hasta la celda **B9**.

2. Compruebe que aparece **$B $9** en el cuadro de texto editable y que la celda **B9** está seleccionada. Si no lo está, haga clic en la celda **B9** para seleccionarla.

3. Haga clic en **OK**.

4. La celda **B9** se convierte en un intervalo denominado `NamedRange1` .

    No hay ninguna indicación visible en la hoja de cálculo, pero `NamedRange1` aparece en el **cuadro Nombre** (justo encima de la hoja de cálculo en el lado izquierdo) cuando se selecciona la celda **B9** .

5. Asegúrese de que **NamedRange1** esté visible en el cuadro de lista nombre de objeto de la ventana **propiedades** y cambie las siguientes propiedades:

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**textFont**|
   |**Valor2**|**Haga clic en una casilla para cambiar el formato de este texto.**|

   A continuación, escriba el código para dar formato al texto cuando se selecciona una opción.

## <a name="format-the-text-when-an-option-is-selected"></a>Dar formato al texto cuando se selecciona una opción
 En esta sección, escribirá código para que cuando el usuario seleccione una opción de formato, se cambie el formato del texto de la hoja de cálculo.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Para cambiar el formato cuando se activa una casilla

1. Haga clic con el botón secundario en **Hoja1** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyBoldFont` casilla:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyItalicFont` casilla:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyUnderlineFont` casilla:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. En C#, debe agregar controladores de eventos para las casillas de verificación al <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que el texto tiene el formato correcto al activar o desactivar una casilla.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Activar o desactivar una casilla.

3. Confirme que el texto tiene el formato correcto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos del uso de las casillas y el formato de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Usar un botón para rellenar un cuadro de texto. Para obtener más información, vea [Tutorial: mostrar texto en un cuadro de texto de una hoja de cálculo mediante un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Consulte también
- [Tutoriales de uso de Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
