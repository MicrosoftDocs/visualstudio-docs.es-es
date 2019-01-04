---
title: 'Tutorial: Recopilación de datos mediante un formulario de Windows'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 11e9b73671a8c4b03c33169739ea8fd02b486568
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926639"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Tutorial: Recopilar datos mediante un formulario de Windows
  En este tutorial se muestra cómo abrir un formulario de Windows Forms desde una personalización de nivel de documento de Microsoft Office Excel, cómo recopilar la información del usuario y cómo escribir dicha información en una celda de la hoja de cálculo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Aunque en este tutorial usaremos específicamente un proyecto de nivel de documento para Excel, los conceptos que se muestran en el mismo se pueden aplicar a otros proyectos de Office.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Crear un proyecto nuevo  
 En primer lugar, es necesario crear un proyecto de libro de Excel.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **WinFormInput**y seleccione **Crear un nuevo documento** en el asistente. Para obtener más información, consulte [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **WinFormInput** al **Explorador de soluciones**.  
  
## <a name="add-a-namedrange-control-to-the-worksheet"></a>Agregar un control NamedRange a la hoja de cálculo  
  
### <a name="to-add-a-named-range-to-sheet1"></a>Agregar un intervalo con nombre a Sheet1  
  
1.  Seleccione la celda **A1** de `Sheet1`.  
  
2.  En el cuadro **Nombre** , escriba **formInput**.  
  
     El cuadro **Nombre** está situado a la izquierda de la barra de fórmulas, justo sobre la columna **A** de la hoja de cálculo.  
  
3.  Presione **ENTRAR**.  
  
     Se agrega un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1**. No hay ninguna indicación visible en la hoja de cálculo, pero **formInput** aparece en el cuadro **Nombre** (justo encima de la hoja de cálculo, en el lado izquierdo) y en la ventana **Propiedades** cuando se selecciona la celda **A1** .  
  
## <a name="add-a-windows-form-to-the-project"></a>Agregue un formulario de Windows para el proyecto  
 Cree un formulario de Windows Forms para solicitar la información al usuario.  
  
### <a name="to-add-a-windows-form"></a>Agregar un formulario de Windows Forms  
  
1. Seleccione el proyecto **WinFormInput** en el **Explorador de soluciones**.  
  
2. En el menú **Proyecto** , haga clic en **Agregar formulario de Windows Forms**.  
  
3. Asigne un nombre al formulario **GetInputString.vb** o **GetInputString.cs**y, a continuación, haga clic en **Agregar**.  
  
    El formulario se abrirá en el diseñador.  
  
4. Agregue un <xref:System.Windows.Forms.TextBox> y un <xref:System.Windows.Forms.Button> al formulario.  
  
5. Seleccione el botón, busque la propiedad **Texto** en la ventana **Propiedades** y cambie el texto a **Aceptar**.  
  
   A continuación, agregue el código a `ThisWorkbook.vb` o a `ThisWorkbook.cs` para recopilar la información del usuario.  
  
## <a name="display-the-windows-form-and-collecting-information"></a>Mostrar el formulario de Windows y la recopilación de la información  
 Cree una instancia del formulario de Windows Forms `GetInputString` y ábrala; a continuación, escriba la información del usuario en una celda de la hoja de cálculo.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Mostrar el formulario y recopilar la información  
  
1. Haga clic con el botón derecho en **ThisWorkbook.vb** o en **ThisWorkbook.cs** en el **Explorador de soluciones**y, a continuación, seleccione **Ver código**.  
  
2. En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Workbook.Open> de `ThisWorkbook`, agregue el siguiente código para declarar una variable del formulario `GetInputString` y hacer que se este se muestre.  
  
   > [!NOTE]  
   >  En C#, debe agregar un controlador de eventos tal como se muestra en el evento <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> que tiene a continuación. Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3. Cree un método llamado `WriteStringToCell` que escriba texto en un intervalo con nombre. La llamada a este método se realiza desde el formulario, y los datos que proporcione el usuario se pasan al control <xref:Microsoft.Office.Tools.Excel.NamedRange> , `formInput`, en la celda **A1**.  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
   A continuación, agregue el código al formulario para controlar el evento “Click” del botón.  
  
## <a name="send-information-to-the-worksheet"></a>Enviar información a la hoja de cálculo  
  
### <a name="to-send-information-to-the-worksheet"></a>Enviar información a la hoja de cálculo  
  
1.  Haga clic con el botón derecho en **GetInputString** , en el **Explorador de soluciones**y, a continuación, seleccione **Diseñador de vistas**.  
  
2.  Haga doble clic en el botón para abrir el archivo de código con el controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón agregado.  
  
3.  Agregue el código al controlador de eventos para obtener los datos incluidos en el cuadro de texto, envíelo a la función `WriteStringToCell`y, a continuación, cierre el formulario.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="test"></a>Prueba  
 Ahora puede ejecutar el proyecto. Aparecerá el formulario de Windows Forms y los datos proporcionados se mostrarán en la hoja de cálculo.  
  
### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Asegúrese que ha aparecido el formulario de Windows Forms.  
  
3.  Escriba **Hello World** en el cuadro de texto y, a continuación, haga clic en **Aceptar**.  
  
4.  Confirme que **Hello World** aparece en la celda **A1** de la hoja de cálculo.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestran los aspectos básicos para mostrar un formulario de Windows Forms y pasar datos a una hoja de cálculo. Entre otras tareas que puede realizar se incluyen las siguientes:  
  
-   Usar los controles de formularios de Windows Forms en un libro de Excel o en un documento de Word. Para obtener más información, consulte [Windows Forms a los controles de información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modificar la interfaz de usuario de una aplicación de Microsoft Office desde una personalización de nivel de documento o un complemento de VSTO. Para obtener más información, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)  
