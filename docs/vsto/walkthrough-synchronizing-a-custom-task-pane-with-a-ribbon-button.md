---
title: Sincronizar el panel de tareas personalizado con el botón de la cinta de opciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad910f94c6b6a4345f6973e84e02c85d4fe1f0e4
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328336"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones
  Este tutorial muestra cómo crear un panel de tareas personalizado que los usuarios puedan ocultar o mostrar haciendo clic en un botón de alternancia en la cinta de opciones. Siempre se debe crear un elemento de interfaz de usuario, como un botón, en el que los usuarios puedan hacer clic para mostrar u ocultar el panel de tareas personalizado, porque las aplicaciones de Microsoft Office no proporcionan una manera predeterminada para que los usuarios muestren u oculten los paneles de tareas personalizados.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Aunque en este tutorial se usa Excel específicamente, los conceptos que se muestran aquí también se aplican a cualquiera de las aplicaciones antes mencionadas.

 En este tutorial se muestran las tareas siguientes:

- Diseñar la interfaz de usuario del panel de tareas personalizado.

- Agregar un botón de alternancia a la cinta de opciones.

- Sincronizar el botón de alternancia con el panel de tareas personalizado.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel o Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Crear el proyecto de complemento
 En este paso, creará un proyecto de complemento VSTO para Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de complemento de Excel con el nombre **SynchronizeTaskPaneAndRibbon**, mediante la plantilla de proyecto complemento de Excel. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código **ThisAddIn.cs** o **ThisAddIn.vb** y agrega el proyecto **SynchronizeTaskPaneAndRibbon** al **Explorador de soluciones**.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Agregar un botón de alternancia a la cinta de opciones
 Una de las instrucciones de diseño de las aplicaciones de Office es que los usuarios siempre deberían tener control de su interfaz de usuario. Para que los usuarios puedan controlar el panel de tareas personalizado, puede agregar un botón de alternancia a la cinta de opciones que muestre y oculte el panel de tareas. Para crear un botón de alternancia, agregue un elemento **Cinta (diseñador visual)** al proyecto. El diseñador ayuda a agregar y colocar controles, a establecer las propiedades del control y a controlar los eventos de control. Para obtener más información, consulte [Diseñador de cinta](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Para agregar un botón de alternancia a la cinta de opciones

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)** .

3. Cambie el nombre de la nueva cinta de opciones por **ManageTaskPaneRibbon**y haga clic en **Agregar**.

     El archivo **ManageTaskPaneRibbon.cs** o **ManageTaskPaneRibbon.vb** se abre en el diseñador de la cinta de opciones y muestra una pestaña y un grupo predeterminados.

4. En el diseñador de la cinta de opciones, haga clic en **group1**para seleccionarlo.

5. En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Administrador de panel de tareas**.

6. En la pestaña **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre **ToggleButton** al grupo **Administrador de panel de tareas** .

7. Haga clic en **toggleButton1**.

8. En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Mostrar panel de tareas**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Diseñar la interfaz de usuario del panel de tareas personalizado
 No hay ningún diseñador visual para los paneles de tareas personalizados, pero puede diseñar un control de usuario según sus gustos. Más adelante en este tutorial, agregará el control de usuario al panel de tareas personalizado.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Para diseñar la interfaz de usuario del panel de tareas personalizado

1. En el menú **Proyecto** , haga clic en **Agregar control de usuario**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , cambie el nombre del control de usuario a **TaskPaneControl**y haga clic en **Agregar**.

     Se abre el control de usuario en el diseñador.

3. En la pestaña **Controles comunes** del **Cuadro de herramientas**, arrastre un control **TextBox** hasta el control de usuario.

## <a name="create-the-custom-task-pane"></a>Crear el panel de tareas personalizado
 Para crear el panel de tareas personalizado cuando se inicia el complemento de VSTO, agregue el control de usuario al panel de tareas en el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> del complemento de VSTO. De forma predeterminada, el panel de tareas personalizado estará oculto. Más adelante en este tutorial, agregará código que muestra u oculta el panel de tareas cuando el usuario hace clic en el botón de alternancia que agregó a la cinta de opciones.

### <a name="to-create-the-custom-task-pane"></a>Para crear el panel de tareas personalizado

1. En el **Explorador de soluciones**, expanda **Excel**.

2. Haga clic con el botón derecho en el archivo **ThisAddin.cs** o **ThisAddin.vb** y luego haga clic en **Ver código**.

3. Agregue el código siguiente a la clase `ThisAddIn` . Este código declara una instancia de `TaskPaneControl` como miembro de `ThisAddIn`.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. Reemplace el controlador de eventos `ThisAddIn_Startup` por el siguiente código: Este código agrega el objeto `TaskPaneControl` al campo `CustomTaskPanes` , pero no muestra el panel de tareas personalizado (de forma predeterminada, la propiedad <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> de la clase <xref:Microsoft.Office.Tools.CustomTaskPane> es **false**). El código de Visual C# también asocia un controlador de eventos al evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> .

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Agregue el método siguiente a la clase `ThisAddIn`. Este método controla el evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> . Cuando el usuario cierra el panel de tareas haciendo clic en el botón **Cerrar** (X), este método actualiza el estado del botón de alternancia en la cinta de opciones.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Agregue la siguiente propiedad a la clase `ThisAddIn` . Esta propiedad expone el objeto `myCustomTaskPane1` privado a otras clases. Más adelante en este tutorial, agregará código a la clase `MyRibbon` que usa esta propiedad.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Ocultar y mostrar el panel de tareas personalizado con el botón de alternancia
 El último paso consiste en agregar código que muestre u oculte el panel de tareas personalizado cuando el usuario haga clic en el botón de alternancia en la cinta de opciones.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Para mostrar y ocultar el panel de tareas personalizado con el botón de alternancia

1. En el diseñador de la cinta de opciones, haga doble clic en el botón de alternancia **Mostrar panel de tareas** .

     Visual Studio genera automáticamente un controlador de eventos denominado `toggleButton1_Click`, que controla el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Visual Studio también abre el archivo *MyRibbon.cs* o *MyRibbon.vb* en el Editor de código.

2. Reemplace el controlador de eventos `toggleButton1_Click` por el siguiente código: Cuando el usuario hace clic en el botón de alternancia, este código muestra u oculta el panel de tareas personalizado, dependiendo de si dicho botón está o no presionado.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Probar el complemento
 Al ejecutar el proyecto, Excel se abre sin mostrar el panel de tareas personalizado. Haga clic en el botón de alternancia en la cinta de opciones para probar el código.

### <a name="to-test-your-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5** para ejecutar el proyecto.

     Confirme que Excel se abre y el **Add-Ins** ficha aparece en la cinta de opciones.

2. Haga clic en el **Add-Ins** pestaña en la cinta de opciones.

3. En el grupo **Administrador del panel de tareas** , haga clic en el botón de alternancia **Mostrar panel de tareas** .

     Compruebe que el panel de tareas se muestra y oculta al hacer clic en el botón de alternancia.

4. Cuando el panel de tareas esté visible, haga clic en el botón **Cerrar** (X) en la esquina del panel de tareas.

     Compruebe que el botón de alternancia aparece como no presionado.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información sobre cómo crear paneles de tareas personalizados en estos temas:

- Crear un panel de tareas personalizado en un complemento de VSTO para una aplicación diferente. Para obtener más información acerca de las aplicaciones que admiten paneles de tareas personalizados, vea [paneles de tareas personalizados](../vsto/custom-task-panes.md).

- Automatizar una aplicación desde un panel de tareas personalizado. Para obtener más información, vea [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Crear un panel de tareas personalizado para cada mensaje de correo que se abre en Outlook. Para obtener más información, vea [Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Vea también
- [Paneles de tareas personalizados](../vsto/custom-task-panes.md)
- [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
