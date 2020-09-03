---
title: 'Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a32cfc84aa9bc93761dc8b57c13651eb04031a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255526"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones
  El diseñador de la cinta de opciones permite crear una pestaña personalizada y, a continuación, agregar y colocar controles en ella.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- [Crear paneles de acciones](#BKMK_CreateActionsPanes).

- [Cree una pestaña personalizada](#BKMK_CreateCustomTab).

- [Ocultar y Mostrar paneles de acciones con los botones de la pestaña personalizada](#BKMK_HideShowActionsPane).

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Crear un proyecto de libro de Excel
 Los pasos para utilizar el diseñador de la cinta de opciones son casi idénticos para todas las aplicaciones de Office. En este ejemplo se utiliza un libro de Excel.

### <a name="to-create-an-excel-workbook-project"></a>Para crear un proyecto de libro de Excel

- Cree un proyecto de libro de Excel con el nombre **MyExcelRibbon**. Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro en el diseñador y agrega el proyecto **MyExcelRibbon** a **Explorador de soluciones**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Crear paneles de acciones
 Agregue dos paneles de acciones personalizados al proyecto. Posteriormente agregará botones a la pestaña personalizada que muestren y oculten estos paneles de acciones.

### <a name="to-create-actions-panes"></a>Para crear paneles de acciones

1. En el menú **Proyecto** , elija **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **ActionsPaneControl**y, a continuación, elija **Agregar**.

     Se abre el archivo **ActionsPaneControl1.CS** o **ActionsPaneControl1. VB** en el diseñador.

3. En la pestaña **controles comunes** del **cuadro de herramientas**, agregue una etiqueta a la superficie del diseñador.

4. En la ventana **propiedades** , establezca la propiedad **texto** de Label1 en **Actions pane 1**.

5. Repita los pasos del 1 al 5 para crear un segundo panel de acciones y una etiqueta. Establezca la propiedad **texto** de la segunda etiqueta en **Actions pane 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Crear una pestaña personalizada
 Una de las instrucciones de diseño de las aplicaciones de Office es que los usuarios siempre deberían tener control de su interfaz de usuario. Para agregar esta capacidad en los paneles de acciones, puede agregar botones que muestren y oculten cada panel de acciones en una pestaña personalizada de la cinta de opciones. Para crear una pestaña personalizada, agregue un elemento **cinta (diseñador visual)** al proyecto. El diseñador ayuda a agregar y colocar controles, a establecer las propiedades del control y a controlar los eventos de control.

### <a name="to-create-a-custom-tab"></a>Para crear una ficha personalizada

1. En el menú **Proyecto** , elija **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.

3. Cambie el nombre de la nueva cinta de opciones a **myribbon**y elija **Agregar**.

     El archivo **MyRibbon.cs** o **MyRibbon.vb** se abre en el diseñador de la cinta de opciones y muestra una ficha y un grupo predeterminados.

4. En el diseñador de la cinta de opciones, elija la pestaña predeterminada.

5. En la ventana **propiedades** , expanda la propiedad **ControlID** y, a continuación, establezca la propiedad **ControlIdType** en **Custom**.

6. Establezca la propiedad **etiqueta** en **mi pestaña personalizada**.

7. En el diseñador de la cinta de opciones, elija **Grupo1**.

8. En la ventana **propiedades** , establezca **etiqueta** en **Actions pane Manager**.

9. En la pestaña controles de la cinta de opciones de **Office** del **cuadro de herramientas**, arrastre un botón hasta **Grupo1**.

10. Seleccione **button1**.

11. En la ventana **propiedades** , establezca **etiqueta** en **Show Actions pane 1**.

12. Agregue un segundo botón a **Grupo1**y establezca la propiedad **etiqueta** en **Show Actions pane 2**.

13. En la pestaña controles de la cinta de opciones de **Office** del **cuadro de herramientas**, arrastre un control **ToggleButton** a **Grupo1**.

14. Establezca la propiedad **etiqueta** en **ocultar panel de acciones**.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Ocultar y Mostrar paneles de acciones con los botones de la pestaña personalizada
 El último paso consiste en agregar código que responda al usuario. Agregue controladores de eventos para los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Agregue código a estos controladores de eventos para ocultar o mostrar los paneles de acciones.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Para ocultar y mostrar paneles de acciones con botones de la ficha personalizada

1. En **Explorador de soluciones**, abra el menú contextual de *MyRibbon.CS* o *myribbon. VB*y, a continuación, elija **Ver código**.

2. Agregue el siguiente código al comienzo de la clase `MyRibbon`. Este código crea dos objetos de panel de acciones.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Reemplace el método `MyRibbon_Load` por el código siguiente. Este código agrega los objetos de panel de acciones a la colección <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> y oculta los objetos de la vista. El código de Visual C# también asocia delegados a varios eventos de control de la cinta de opciones.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Agregue los tres métodos de control de eventos siguientes a la clase `MyRibbon`. Estos métodos controlan los eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> de los dos botones y el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Los controladores de eventos de button1 y button2 muestran paneles de acciones alternativos. El controlador de eventos de toggleButton1 muestra y oculta el panel de acciones activo.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Prueba de la pestaña personalizada
 Al ejecutar el proyecto, se inicia Excel y aparece la pestaña **mi pestaña personalizada** en la cinta de opciones. Elija los botones de la **pestaña personalizado** para mostrar y ocultar los paneles de acciones.

### <a name="to-test-the-custom-tab"></a>Para probar la ficha personalizada

1. Presione **F5** para ejecutar el proyecto.

2. Elija la pestaña **mi pestaña personalizada** .

3. En el grupo **Custom Actions pane Manager** , elija **Show Actions pane 1**.

     El panel de acciones aparece y muestra la etiqueta **Actions pane 1**.

4. Elija **Mostrar el panel 2 de acciones**.

     El panel de acciones aparece y muestra la etiqueta **Actions pane 2**.

5. Elija **ocultar panel de acciones**.

     Los paneles de acciones ya no están visibles.

## <a name="next-steps"></a>Pasos siguientes
 Puede aprender más acerca de la personalización de la interfaz de usuario de Office en estos temas:

- Agregar una interfaz de usuario basada en contexto a cualquier personalización de nivel de documento. Para obtener más información, vea [información general del panel de acciones](../vsto/actions-pane-overview.md).

- Extender un formulario estándar o personalizado de Microsoft Office Outlook. Para obtener más información, vea [Tutorial: diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Consulte también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Personalización de una cinta para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Cómo cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Información general del modelo de objetos de la cinta](../vsto/ribbon-object-model-overview.md)
