---
title: Mostrar texto en el cuadro de texto de la hoja de cálculo mediante el botón
description: Conozca los conceptos básicos del uso de botones y cuadros de texto en hojas de cálculo de Microsoft Excel. Cree también proyectos de Excel mediante las herramientas de desarrollo de Office Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827791"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo mediante un botón
  En este tutorial se muestran los conceptos básicos del uso de botones y cuadros de texto en hojas de cálculo Microsoft Office Excel y cómo crear proyectos de Excel mediante herramientas de desarrollo de Office en Visual Studio. Para ver el resultado como un ejemplo completado, vea los ejemplos y tutoriales de Ejemplo de controles de Excel [en Office.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante este tutorial aprenderá a:

- Agregar controles a una hoja de cálculo.

- Rellene un cuadro de texto cuando se haga clic en un botón.

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

1. Cree un proyecto de libro de Excel con el nombre **Mi botón de Excel**. Asegúrese de que **está seleccionada la opción Crear** un documento nuevo. Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **proyecto Mi botón de Excel** a **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 Para este tutorial, necesitará un botón y un cuadro de texto en la primera hoja de cálculo.

### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto

1. Compruebe que el **libro My Excel Button.xlsx** está abierto en el diseñador Visual Studio, con la vista `Sheet1` mostrada.

2. En la **pestaña Controles comunes** del Cuadro de herramientas, arrastre a <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> `Sheet1` .

3. En el **menú Ver,** seleccione **Ventana Propiedades**.

4. Asegúrese de que **TextBox1**  esté visible en el cuadro desplegable ventana Propiedades y cambie la propiedad **Name** del cuadro de texto **a displayText**.

5. Arrastre un control **Botón** a `Sheet1` y cambie las siguientes propiedades:

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**insertText**|
   |**Texto**|**Insertar texto**|

   Ahora escriba el código para ejecutarlo cuando se haga clic en el botón.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se hace clic en el botón
 Cada vez que el usuario hace clic en el **botón, Hola mundo.** se anexa al cuadro de texto.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón

1. En **Explorador de soluciones**, haga clic con el botón derecho **en Hoja1** y, a continuación, haga clic **en Ver código** en el menú contextual.

2. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos del botón:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. En C#, debe agregar un controlador de eventos al <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para asegurarse de que el mensaje **Hola mundo.** aparece en el cuadro de texto al hacer clic en el botón.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Haga clic en el botón.

3. Confirme que **Hola mundo.** aparece en el cuadro de texto.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos del uso de botones y cuadros de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:

- Implementación del proyecto. Para obtener más información, vea [Implementar una solución de Office.](../vsto/deploying-an-office-solution.md)

- Uso de casillas para cambiar el formato. Para obtener más información, vea [Tutorial: Cambiar el formato de la hoja de cálculo mediante controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Consulte también
- [Cómo: Agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Tutoriales con Excel](../vsto/walkthroughs-using-excel.md)
- [Limitaciones de los Windows Forms controles en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
