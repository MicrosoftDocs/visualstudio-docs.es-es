---
title: Cambiar el formato de la hoja de cálculo mediante controles CheckBox
description: Obtenga información sobre cómo puede usar las herramientas de desarrollo de Office Visual Studio para crear y agregar código al proyecto.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6f649fad99b8d94cc650ecda57e10b423b14194e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826439"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Tutorial: Cambiar el formato de la hoja de cálculo mediante controles CheckBox
  En este tutorial se muestran los aspectos básicos del uso de casillas en una hoja Microsoft Office excel para cambiar el formato. Usará las herramientas de desarrollo de Office en Visual Studio para crear y agregar código al proyecto. Para ver el resultado como un ejemplo completado, vea los ejemplos y tutoriales de Ejemplo de controles de Excel [en Office.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregue texto y controles a una hoja de cálculo.

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

1. Cree un proyecto de libro de Excel con el nombre **My Excel Formatting**. Asegúrese de que **está seleccionada la opción Crear** un documento nuevo. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **proyecto My Excel Formatting** (Mi formato de Excel) a **Explorador de soluciones**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Agregar texto y controles a la hoja de cálculo
 Para este tutorial, necesitará tres <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controles y texto en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-add-three-check-boxes"></a>Para agregar tres casillas

1. Compruebe que el libro está abierto en el diseñador Visual Studio y `Sheet1` que está abierto.

2. En la **pestaña Controles comunes** del Cuadro **de** herramientas , arrastre un control a la celda B2 de Sheet1 o cerca <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> de **esta.** 

3. En el **menú Ver,** seleccione la **ventana** Propiedades.

4. Asegúrese de que **Checkbox1 esté** visible en el cuadro de lista nombre de objeto de **la** ventana Propiedades y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyBoldFont**|
    |**Texto**|**Negrita**|

5. Arrastre una segunda casilla en la celda **B4** o cerca de esta y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyItalicFont**|
    |**Texto**|**Cursiva**|

6. Arrastre una tercera casilla en la celda **B6** o cerca de esta y cambie las siguientes propiedades:

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**applyUnderlineFont**|
    |**Texto**|**Subrayar**|

7. Active los tres controles de casilla mientras mantiene **presionada la tecla Ctrl.**

8. En el grupo Organizar de la pestaña Formato de Excel, haga clic **en Alinear** y, a continuación, haga clic en Alinear a **la izquierda.**

     Los tres controles de casilla se alinean en el lado izquierdo, en la posición del primer control seleccionado.

     A continuación, arrastrará un control a <xref:Microsoft.Office.Tools.Excel.NamedRange> la hoja de cálculo.

    > [!NOTE]
    > También puede agregar el <xref:Microsoft.Office.Tools.Excel.NamedRange> control escribiendo **textFont** en el **cuadro** Nombre.

#### <a name="to-add-text-to-a-namedrange-control"></a>Para agregar texto a un control NamedRange

1. En la **pestaña Controles de Excel** del cuadro de herramientas, arrastre un control a la celda <xref:Microsoft.Office.Tools.Excel.NamedRange> **B9.**

2. Compruebe que **$B$9** aparece en el cuadro de texto editable y que la **celda B9** está seleccionada. Si no es así, haga clic en la **celda B9** para seleccionarla.

3. Haga clic en **OK**.

4. La **celda B9** se convierte en un intervalo denominado `NamedRange1` .

    No hay ninguna indicación visible en la hoja de cálculo, pero aparece en el cuadro Nombre (justo encima de la hoja de cálculo del lado izquierdo) cuando se selecciona `NamedRange1` la celda **B9.** 

5. Asegúrese de que **NamedRange1 está** visible en el cuadro de lista nombre de objeto de la ventana **Propiedades** y cambie las siguientes propiedades:

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**textFont**|
   |**Valor2**|**Haga clic en una casilla para cambiar el formato de este texto.**|

   A continuación, escriba el código para dar formato al texto cuando se seleccione una opción.

## <a name="format-the-text-when-an-option-is-selected"></a>Dar formato al texto cuando se selecciona una opción
 En esta sección, escribirá código para que cuando el usuario seleccione una opción de formato, se cambie el formato del texto de la hoja de cálculo.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Para cambiar el formato cuando se selecciona una casilla

1. Haga clic con el botón **derecho en Hoja1** y, a continuación, haga clic **en Ver código** en el menú contextual.

2. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyBoldFont` casilla:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyItalicFont` casilla:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos de la `applyUnderlineFont` casilla:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. En C#, debe agregar controladores de eventos para las casillas al <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que el texto tiene el formato correcto al activar o borrar una casilla.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Activar o desactivar una casilla.

3. Confirme que el formato del texto es correcto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos del uso de casillas y el formato de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:

- Implementación del proyecto. Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- Usar un botón para rellenar un cuadro de texto. Para obtener más información, vea [Tutorial: Mostrar texto en](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)un cuadro de texto en una hoja de cálculo mediante un botón .

## <a name="see-also"></a>Consulte también
- [Tutoriales con Excel](../vsto/walkthroughs-using-excel.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Limitaciones de los Windows Forms controles en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
