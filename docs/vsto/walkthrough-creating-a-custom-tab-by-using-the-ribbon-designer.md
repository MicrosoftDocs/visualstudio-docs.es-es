---
title: 'Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7fdae2b6a867b6d87c6579fc1d24f9d0ebd07cf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones
  El diseñador de la cinta de opciones permite crear una pestaña personalizada y, a continuación, agregar y colocar controles en ella.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   [Crear paneles de acciones](#BKMK_CreateActionsPanes).  
  
-   [Crear una pestaña personalizada](#BKMK_CreateCustomTab).  
  
-   [Ocultar y mostrar paneles de acciones con botones de la ficha personalizada](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Crear un proyecto de libro de Excel  
 Los pasos para utilizar el diseñador de la cinta de opciones son casi idénticos para todas las aplicaciones de Office. En este ejemplo se utiliza un libro de Excel.  
  
#### <a name="to-create-an-excel-workbook-project"></a>Para crear un proyecto de libro de Excel  
  
-   Cree un proyecto de libro de Excel con el nombre **MyExcelRibbon**. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro en el diseñador y agrega el **MyExcelRibbon** proyecto al **el Explorador de soluciones**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Crear paneles de acciones  
 Agregue dos paneles de acciones personalizados al proyecto. Posteriormente agregará botones a la pestaña personalizada que muestren y oculten estos paneles de acciones.  
  
#### <a name="to-create-actions-panes"></a>Para crear paneles de acciones  
  
1.  En el menú **Proyecto** , elija **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **ActionsPaneControl**y, a continuación, elija **agregar**.  
  
     El **ActionsPaneControl1.cs** o **ActionsPaneControl1.vb** archivo se abre en el diseñador.  
  
3.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, agregue una etiqueta a la superficie del diseñador.  
  
4.  En el **propiedades** ventana, establezca el **texto** propiedad de label1 en **Actions Pane 1**.  
  
5.  Repita los pasos del 1 al 5 para crear un segundo panel de acciones y una etiqueta. Establecer el **texto** propiedad de la segunda etiqueta a **Actions Pane 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a> Crear una ficha personalizada  
 Una de las instrucciones de diseño de las aplicaciones de Office es que los usuarios siempre deberían tener control de su interfaz de usuario. Para agregar esta capacidad en los paneles de acciones, puede agregar botones que muestren y oculten cada panel de acciones en una pestaña personalizada de la cinta de opciones. Para crear una ficha personalizada, agregue un **cinta (diseñador Visual)** al proyecto. El diseñador ayuda a agregar y colocar controles, a establecer las propiedades del control y a controlar los eventos de control.  
  
#### <a name="to-create-a-custom-tab"></a>Para crear una ficha personalizada  
  
1.  En el menú **Proyecto** , elija **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.  
  
3.  Cambiar el nombre de la nueva cinta de opciones para **MyRibbon**y elija **agregar**.  
  
     El archivo **MyRibbon.cs** o **MyRibbon.vb** se abre en el diseñador de la cinta de opciones y muestra una ficha y un grupo predeterminados.  
  
4.  En el diseñador de la cinta de opciones, elija la pestaña predeterminada.  
  
5.  En el **propiedades** ventana, expanda la **ControlId** propiedad y, a continuación, establezca el **ControlIdType** propiedad **personalizado**.  
  
6.  Establecer el **etiqueta** propiedad **My Custom Tab**.  
  
7.  En el Diseñador de la cinta de opciones, elija **group1**.  
  
8.  En el **propiedades** ventana, establezca **etiqueta** a **Actions Pane Manager**.  
  
9. Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre un botón hasta **group1**.  
  
10. Seleccione **button1**.  
  
11. En el **propiedades** ventana, establezca **etiqueta** a **Show Actions Pane 1**.  
  
12. Agregue un segundo botón a **group1**y establezca el **etiqueta** propiedad **Show Actions Pane 2**.  
  
13. Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre un **ToggleButton** control **group1**.  
  
14. Establecer el **etiqueta** propiedad **Hide Actions Pane**.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Ocultar y mostrar paneles de acciones con botones de la ficha personalizada  
 El último paso consiste en agregar código que responda al usuario. Agregue controladores de eventos para los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Agregue código a estos controladores de eventos para ocultar o mostrar los paneles de acciones.  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Para ocultar y mostrar paneles de acciones con botones de la ficha personalizada  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de MyRibbon.cs o MyRibbon.vb y, a continuación, elija **ver código**.  
  
2.  Agregue el siguiente código al comienzo de la clase `MyRibbon`. Este código crea dos objetos de panel de acciones.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Reemplace el método `MyRibbon_Load` por el código siguiente. Este código agrega los objetos de panel de acciones a la colección <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> y oculta los objetos de la vista. El código de Visual C# también asocia delegados a varios eventos de control de la cinta de opciones.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Agregue los tres métodos de control de eventos siguientes a la clase `MyRibbon`. Estos métodos controlan los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Los controladores de eventos de button1 y button2 muestran paneles de acciones alternativos. El controlador de eventos de toggleButton1 muestra y oculta el panel de acciones activo.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>Probar la ficha personalizada  
 Al ejecutar el proyecto, se inicia Excel y el **My Custom Tab** ficha aparece en la cinta de opciones. Elija los botones de **My Custom Tab** para mostrar y ocultar los paneles de acciones.  
  
#### <a name="to-test-the-custom-tab"></a>Para probar la ficha personalizada  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Elija la **My Custom Tab** ficha.  
  
3.  En el **Custom Actions Pane Manager** grupo, elija **Show Actions Pane 1**.  
  
     El panel de acciones aparece y muestra la etiqueta **Actions Pane 1**.  
  
4.  Elija **Show Actions Pane 2**.  
  
     El panel de acciones aparece y muestra la etiqueta **Actions Pane 2**.  
  
5.  Elija **ocultar panel de acciones**.  
  
     Los paneles de acciones ya no están visibles.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:  
  
-   Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento. Para obtener más información, consulta [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Extender un formulario estándar o personalizado de Microsoft Office Outlook. Para obtener más información, consulte [Tutorial: diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Vea también  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Información general sobre el modelo de objetos para la cinta](../vsto/ribbon-object-model-overview.md)  
  
  