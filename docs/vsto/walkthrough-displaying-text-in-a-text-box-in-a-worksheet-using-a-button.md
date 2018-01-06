---
title: "Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7743a3d1c0548b444343b3dc96b25eabac4ac951
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón
  En este tutorial se muestra los aspectos básicos del uso de botones y cuadros de texto en hojas de cálculo de Microsoft Office Excel y cómo crear proyectos de Excel con las herramientas de desarrollo de Office en Visual Studio. Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Excel en [ejemplos de desarrollo de Office y tutoriales](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Rellenar un cuadro de texto cuando se hace clic en un botón.  
  
-   El proyecto de prueba.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 En este paso, creará un proyecto de libro de Excel con Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi botón de Excel**. Asegúrese de que **crear un nuevo documento** está seleccionada. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi botón de Excel** proyecto al **el Explorador de soluciones**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 En este tutorial, necesitará un botón y un cuadro de texto en la primera hoja de cálculo.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Para agregar un botón y un cuadro de texto  
  
1.  Compruebe que la **mi Button.xlsx de Excel** libro está abierto en el Diseñador de Visual Studio, con `Sheet1` muestra.  
  
2.  Desde el **controles comunes** ficha del cuadro de herramientas, arrastre un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> a `Sheet1`.  
  
3.  Desde el **vista** menú, seleccione **ventana propiedades**.  
  
4.  Asegúrese de que **TextBox1** está visible en el **propiedades** cuadro de lista desplegable de la ventana y cambie la **nombre** propiedad del cuadro de texto para **displayText**.  
  
5.  Arrastre un **botón** control `Sheet1` y cambie las siguientes propiedades:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**Texto**|**Insertar texto**|  
  
 Ahora, escriba el código que se ejecuta cuando se hace clic en el botón.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Rellenar el cuadro de texto cuando se hace clic en el botón  
 Cada vez que el usuario hace clic en el botón **Hello World!** se anexa al cuadro de texto.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Para escribir en el cuadro de texto cuando se haga clic en el botón  
  
1.  En **el Explorador de soluciones**, haga clic en **Sheet1**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  En C#, debe agregar un controlador de eventos para el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eventos tal y como se muestra a continuación. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que el mensaje **Hello World!** aparece en el cuadro de texto al hacer clic en el botón.  
  
#### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Haga clic en el botón.  
  
3.  Confirme que **Hola a todos!** aparece en el cuadro de texto.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del uso de botones y cuadros de texto en hojas de cálculo de Excel. A continuación, podría realizar las siguientes tareas:  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Mediante las casillas de verificación para cambiar el formato. Para obtener más información, consulte [Tutorial: cambiar hoja de cálculo formato utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar controles a documentos de Office de Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitaciones de los controles de Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  