---
title: 'Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: adc12d920fd3dc128bf23f92508fef8d239b4e8d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935104"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox
  En este tutorial se muestra los aspectos básicos del uso de las casillas de verificación en una hoja de cálculo de Microsoft Office Excel para cambiar el formato. Utilizará las herramientas de desarrollo de Office en Visual Studio para crear y agregar código al proyecto. Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Excel en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar texto y controles a una hoja de cálculo.  
  
-   Dar formato al texto cuando se selecciona una opción.  
  
-   Pruebe el proyecto.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Crear el proyecto  
 En este paso, creará un proyecto de libro de Excel mediante el uso de Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi formato de Excel**. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi formato de Excel** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>Agregar texto y controles a la hoja de cálculo  
 En este tutorial, necesitará tres <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controles y texto en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control.  
  
### <a name="to-add-three-check-boxes"></a>Para agregar tres casillas de verificación  
  
1.  Compruebe que el libro está abierto en el Diseñador de Visual Studio y que `Sheet1` está abierto.  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> control en o cerca de la celda **B2** en **Sheet1**.  
  
3.  Desde el **vista** menú, seleccione **propiedades** ventana.  
  
4.  Asegúrese de que **Checkbox1** está visible en el cuadro de lista Nombre de objeto de la **propiedades** ventana y cambie las siguientes propiedades:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Texto**|**Negrita**|  
  
5.  Arrastre una segunda casilla en o cerca de la celda **B4** y cambiar las propiedades siguientes:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Texto**|**Cursiva**|  
  
6.  Arrastre una tercera casilla en o cerca de la celda **B6** y cambiar las propiedades siguientes:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Texto**|**Subrayado**|  
  
7.  Seleccione todos los controles de casilla de verificación tres mientras mantiene la **Ctrl** clave.  
  
8.  En el grupo de organización de la pestaña de formato de Excel, haga clic en **alinear**y, a continuación, haga clic en **Alinear a la izquierda**.  
  
     Los controles de casilla de verificación tres se alinean a la izquierda, en la posición del primer control seleccionado.  
  
     A continuación, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la hoja de cálculo.  
  
    > [!NOTE]  
    >  También puede agregar el <xref:Microsoft.Office.Tools.Excel.NamedRange> control escribiendo **textFont** en el **nombre** cuadro.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Para agregar texto a un control NamedRange  
  
1. Desde el **controles de Excel** ficha del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a la celda **B9**.  
  
2. Compruebe que **$B$ 9** aparece en el cuadro de texto editable y esa celda **B9** está seleccionada. Si no es así, haga clic en la celda **B9** para seleccionarlo.  
  
3. Haga clic en **Aceptar**.  
  
4. Celda **B9** se convierte en un rango con nombre `NamedRange1`.  
  
    No hay ninguna indicación visible en la hoja de cálculo, pero `NamedRange1` aparece en el **cuadro nombre** (justo encima de la hoja de cálculo en el lado izquierdo) cuando la celda **B9** está seleccionada.  
  
5. Asegúrese de que **NamedRange1** está visible en el cuadro de lista Nombre de objeto de la **propiedades** ventana y cambie las siguientes propiedades:  
  
   |Property|Valor|  
   |--------------|-----------|  
   |**Name**|**textFont**|  
   |**Value2**|**Haga clic en una casilla de verificación para cambiar el formato de este texto.**|  
  
   A continuación, escriba el código para dar formato al texto cuando se selecciona una opción.  
  
## <a name="format-the-text-when-an-option-is-selected"></a>Dar formato al texto cuando se selecciona una opción  
 En esta sección, escribirá código para que cuando el usuario selecciona una opción de formato, se cambia el formato del texto en la hoja de cálculo.  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Para cambiar el formato cuando una casilla de verificación está seleccionada  
  
1.  Haga clic en **Sheet1**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyBoldFont` casilla de verificación:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyItalicFont` casilla de verificación:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la `applyUnderlineFont` casilla de verificación:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  En C#, debe agregar controladores de eventos para las casillas de verificación a la <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento tal como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar su libro para asegurarse de que el texto se formateó correctamente cuando se activa o desactiva una casilla de verificación.  
  
### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Active o desactive una casilla de verificación.  
  
3.  Confirme que el texto se formateó correctamente.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del uso de las casillas de verificación y dar formato al texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
-   Usar un botón para rellenar un cuadro de texto. Para obtener más información, vea [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
