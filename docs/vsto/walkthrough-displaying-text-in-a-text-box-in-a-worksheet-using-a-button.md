---
title: 'Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ff8bdde07844da26b03bca45f41887d6b4eb64ef
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863830"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón
  En este tutorial se muestra los aspectos básicos del uso de botones y cuadros de texto en hojas de cálculo de Microsoft Office Excel y cómo crear proyectos de Excel con herramientas de desarrollo de Office en Visual Studio. Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Excel en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Rellenar un cuadro de texto cuando se hace clic en un botón.  
  
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
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi botón de Excel**. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi botón de Excel** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 En este tutorial, necesitará un botón y un cuadro de texto en la primera hoja de cálculo.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto  
  
1. Compruebe que la **mi Button.xlsx Excel** libro está abierto en el Diseñador de Visual Studio, con `Sheet1` muestra.  
  
2. Desde el **controles comunes** ficha del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> a `Sheet1`.  
  
3. Desde el **vista** menú, seleccione **ventana propiedades**.  
  
4. Asegúrese de que **TextBox1** está visible en el **propiedades** cuadro de lista desplegable de la ventana y cambie el **nombre** propiedad del cuadro de texto a **displayText**.  
  
5. Arrastre un **botón** control `Sheet1` y cambiar las propiedades siguientes:  
  
   |Property|Valor|  
   |--------------|-----------|  
   |**Name**|**insertText**|  
   |**Texto**|**Insertar texto**|  
  
   Ahora, escriba el código que se ejecuta cuando se hace clic en el botón.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se hace clic en el botón  
 Cada vez que el usuario hace clic en el botón, **Hello World!** se anexa al cuadro de texto.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón  
  
1.  En **el Explorador de soluciones**, haga clic en **Sheet1**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  En C#, debe agregar un controlador de eventos para el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento tal como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que el mensaje **Hello World!** aparece en el cuadro de texto al hacer clic en el botón.  
  
### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Haga clic en el botón.  
  
3.  Confirme que **Hola a todos!** aparece en el cuadro de texto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del uso de botones y cuadros de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilice las casillas de verificación para cambiar el formato. Para obtener más información, vea [Tutorial: Cambiar formato de hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
