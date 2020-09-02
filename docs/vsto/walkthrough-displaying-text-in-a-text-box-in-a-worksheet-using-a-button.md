---
title: Mostrar texto en el cuadro de texto de la hoja de cálculo con el botón
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
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328718"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Tutorial: mostrar texto en un cuadro de texto de una hoja de cálculo mediante un botón
  En este tutorial se muestran los aspectos básicos del uso de botones y cuadros de texto en Microsoft Office hojas de cálculo de Excel y cómo crear proyectos de Excel con las herramientas de desarrollo de Office en Visual Studio. Para ver el resultado como un ejemplo completado, vea el ejemplo de controles de Excel en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar controles a una hoja de cálculo.

- Rellenar un cuadro de texto cuando se hace clic en un botón.

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

1. Cree un proyecto de libro de Excel con el nombre **mi botón de Excel**. Asegúrese de que **la opción crear un nuevo documento** está seleccionada. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto de **botón mi Excel** a **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 En este tutorial, necesitará un botón y un cuadro de texto en la primera hoja de cálculo.

### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto

1. Compruebe que el libro **mis Excel Button.xlsx** está abierto en el diseñador de Visual Studio, con la `Sheet1` muestra.

2. En la pestaña **controles comunes** del cuadro de herramientas, arrastre <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> hasta `Sheet1` .

3. En el menú **Ver** , seleccione **ventana Propiedades**.

4. Asegúrese de que **textBox1** esté visible en el cuadro desplegable de la ventana **propiedades** y cambie la propiedad **nombre** del cuadro de texto a **textoparamostrar**.

5. Arrastre un control de **botón** hasta `Sheet1` y cambie las propiedades siguientes:

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**insertText**|
   |**Texto**|**Insertar texto**|

   Ahora escriba el código que se ejecutará cuando se haga clic en el botón.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se haga clic en el botón
 Cada vez que el usuario haga clic en el botón, **Hola mundo!** se anexa al cuadro de texto.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón

1. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1**y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. En C#, debe agregar un controlador de eventos al <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, tal y como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que el mensaje **Hola mundo.** aparece en el cuadro de texto al hacer clic en el botón.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Haga clic en el botón.

3. Confirme que **Hola mundo!** aparece en el cuadro de texto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos del uso de botones y cuadros de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

- Usar casillas para cambiar el formato. Para obtener más información, vea [Tutorial: cambiar el formato de una hoja de cálculo mediante controles de casilla](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Consulte también
- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Tutoriales de uso de Excel](../vsto/walkthroughs-using-excel.md)
- [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
