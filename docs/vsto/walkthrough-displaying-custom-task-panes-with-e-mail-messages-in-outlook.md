---
title: 'Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c25121e96005486450397938aad3c24f89d26cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828473"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook
  Este tutorial muestra cómo mostrar una instancia única de cada mensaje de correo electrónico que se crea o abre un panel de tareas personalizado. Los usuarios pueden mostrar u ocultar el panel de tareas personalizado mediante un botón de la cinta de opciones de cada mensaje de correo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Para mostrar un panel de tareas personalizado con varias ventanas de explorador o inspector, es necesario crear una instancia del panel de tareas personalizado para cada ventana que se abra. Para obtener más información sobre el comportamiento de los paneles de tareas personalizados en ventanas de Outlook, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  En este tutorial se presenta el código del complemento de VSTO en pequeñas secciones para que resulte más fácil explicar la lógica detrás del código.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Diseñar la interfaz de usuario (UI) del panel de tareas personalizado.  
  
-   Crear una interfaz de usuario de cinta de opciones personalizada.  
  
-   Mostrar la interfaz de usuario de cinta de opciones personalizada con mensajes de correo electrónico.  
  
-   Crear una clase para administrar ventanas de inspector y paneles de tareas personalizados.  
  
-   Inicializar y limpiar los recursos usados por el complemento de VSTO.  
  
-   Sincronizar el botón de alternancia de la cinta de opciones con el panel de tareas personalizado.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o Microsoft Outlook 2010.  
  
  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo los paneles de tareas: uso de Outlook?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="create-the-project"></a>Crear el proyecto  
 Los paneles de tareas personalizados se implementan en complementos de VSTO. Empiece por crear un proyecto de complemento VSTO para Outlook.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Crear un proyecto **Complemento de Outlook** con el nombre **OutlookMailItemTaskPane**. Use la plantilla de proyecto **Complemento de Outlook** . Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código *ThisAddIn.cs* o *ThisAddIn.vb* y agrega el proyecto **OutlookMailItemTaskPane** al **Explorador de soluciones**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Diseñar la interfaz de usuario del panel de tareas personalizado  
 No hay ningún diseñador visual para los paneles de tareas personalizados, pero puede diseñar un control de usuario con la interfaz de usuario que desee. El panel de tareas personalizado de este complemento de VSTO tiene una interfaz de usuario simple que contiene un control <xref:System.Windows.Forms.TextBox> . Más adelante en este tutorial, agregará el control de usuario al panel de tareas personalizado.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Para diseñar la interfaz de usuario del panel de tareas personalizado  
  
1.  En el **Explorador de soluciones**, haga clic en el proyecto **OutlookMailItemTaskPane** .  
  
2.  En el menú **Proyecto** , haga clic en **Agregar control de usuario**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento** , cambie el nombre del control de usuario a **TaskPaneControl**y haga clic en **Agregar**.  
  
     Se abre el control de usuario en el diseñador.  
  
4.  En la pestaña **Controles comunes** del **Cuadro de herramientas**, arrastre un control **TextBox** hasta el control de usuario.  
  
## <a name="design-the-user-interface-of-the-ribbon"></a>Diseñar la interfaz de usuario de la cinta de opciones  
 Uno de los objetivos de este complemento VSTO es proporcionar a los usuarios una manera de ocultar o mostrar el panel de tareas personalizado en la cinta de opciones de cada mensaje de correo electrónico. Para proporcionar la interfaz de usuario, cree una interfaz de usuario de cinta de opciones personalizada que muestre un botón de alternancia en el que los usuarios pueden hacer clic para mostrar u ocultar el panel de tareas personalizado.  
  
### <a name="to-create-a-custom-ribbon-ui"></a>Para crear una interfaz de usuario de cinta de opciones personalizada  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.  
  
3.  Cambie el nombre de la nueva cinta de opciones por **ManageTaskPaneRibbon**y haga clic en **Agregar**.  
  
     El archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* se abre en el diseñador de la cinta de opciones y muestra una pestaña y un grupo predeterminados.  
  
4.  En el diseñador de la cinta de opciones, haga clic en **group1**para seleccionarlo.  
  
5.  En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Administrador de panel de tareas**.  
  
6.  En la pestaña **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre un control ToggleButton al grupo **Administrador de panel de tareas** .  
  
7.  Haga clic en **toggleButton1**.  
  
8.  En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Mostrar panel de tareas**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Mostrar la interfaz de usuario de cinta de opciones personalizada con mensajes de correo electrónico  
 El panel de tareas personalizado que va a crear en este tutorial se ha diseñado para que aparezca únicamente con las ventanas de inspector que contienen mensajes de correo. Por lo tanto, debe definir las propiedades de forma que la interfaz de usuario de la cinta de opciones personalizada solo aparezca con estas ventanas.  
  
### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Para mostrar la interfaz de usuario de cinta de opciones personalizada con mensajes de correo electrónico  
  
1.  En el diseñador de la cinta de opciones, haga clic en la cinta **ManageTaskPaneRibbon** .  
  
2.  En la ventana **Propiedades** , haga clic en la lista desplegable situada junto a **RibbonType**y seleccione **Microsoft.Outlook.Mail.Compose** y **Microsoft.Outlook.Mail.Read**.  
  
## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Crear una clase para administrar ventanas de inspector y paneles de tareas personalizados  
 Hay varios casos en que el complemento de VSTO debe identificar qué panel de tareas personalizado está asociado con un mensaje de correo electrónico específico. Estos casos son los siguientes:  
  
- Cuando el usuario cierra un mensaje de correo electrónico. En este caso, el complemento de VSTO debe quitar el panel de tareas personalizado correspondiente para garantizar que los recursos usados por el complemento de VSTO se limpian correctamente.  
  
- Cuando el usuario cierra el panel de tareas personalizado. En este caso, el complemento de VSTO debe actualizar el estado del botón de alternancia en la cinta de opciones de mensaje de correo electrónico.  
  
- Cuando el usuario hace clic en el botón de alternancia en la cinta de opciones. En este caso, el complemento de VSTO debe ocultar o mostrar el panel de tareas correspondiente.  
  
  Para habilitar el complemento VSTO realizar un seguimiento de qué panel de tareas personalizado está asociado con cada mensaje de correo electrónico abierto, cree una clase personalizada que contenga pares de <xref:Microsoft.Office.Interop.Outlook.Inspector> y <xref:Microsoft.Office.Tools.CustomTaskPane> objetos. Esta clase crea un nuevo objeto de panel de tareas personalizado para cada mensaje de correo electrónico, y elimina el panel de tareas personalizado cuando se cierra el correspondiente mensaje de correo electrónico.  
  
### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Para crear una clase para administrar ventanas de inspector y paneles de tareas personalizados  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo *ThisAddIn.vb* o *ThisAddIn.cs* y luego haga clic en **Ver código**.  
  
2.  Agregue las instrucciones siguientes en la parte superior del archivo.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Agregue el código siguiente al archivo *ThisAddIn.cs* o *ThisAddIn.vb* , fuera la clase `ThisAddIn` (para Visual C#, agregue este código dentro del espacio de nombres `OutlookMailItemTaskPane` ). La clase `InspectorWrapper` administra un par de objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> y <xref:Microsoft.Office.Tools.CustomTaskPane> . Completará la definición de esta clase en los pasos siguientes.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Agregue el constructor siguiente después del código que agregó en el paso anterior. Este constructor crea e inicializa un nuevo panel de tareas personalizado que está asociado al objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que se pasa. En C#, el constructor asocia también controladores de eventos al evento <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> del objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> y al evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> del objeto <xref:Microsoft.Office.Tools.CustomTaskPane> .  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Agregue el método siguiente después del código que agregó en el paso anterior. Este método es un controlador de eventos para el evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> de objeto <xref:Microsoft.Office.Tools.CustomTaskPane> que se encuentra en la clase `InspectorWrapper` . Este código actualiza el estado del botón de alternancia cada vez que el usuario abre o cierra el panel de tareas personalizado.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Agregue el método siguiente después del código que agregó en el paso anterior. Este método es un controlador de eventos para el <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> eventos de la <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto que contiene el mensaje de correo electrónico actual. El controlador de eventos libera los recursos cuando se cierra el mensaje de correo electrónico. El controlador de eventos también quita el panel de tareas personalizado actual desde la colección `CustomTaskPanes` . Esto ayuda a evitar que varias instancias del panel de tareas personalizado cuando se abre el siguiente mensaje de correo electrónico.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Agregue el código siguiente después del código que agregó en el paso anterior. Más adelante en este tutorial, llamará a esta propiedad desde un método de la interfaz de usuario de la cinta de opciones para mostrar u ocultar el panel de tareas personalizado.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicializar y limpiar los recursos utilizados por el complemento  
 Agregue código a la clase `ThisAddIn` para inicializar el complemento de VSTO cuando este se cargue y para limpiar los recursos cuando dicho complemento se descargue. Inicializar el complemento de VSTO mediante la configuración de un controlador de eventos para el <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> eventos y pase todos los mensajes de correo electrónico existentes a este controlador de eventos. Una vez que se descargue el complemento de VSTO, desasocie el controlador de eventos y limpie los objetos utilizados por el complemento de VSTO.  
  
### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Para inicializar y limpiar los recursos usados por el complemento de VSTO  
  
1. En el archivo *ThisAddIn.cs* o *ThisAddIn.vb* , busque la definición de la clase `ThisAddIn` .  
  
2. Agregue las declaraciones siguientes a la clase `ThisAddIn` :  
  
   - El campo `inspectorWrappersValue` contiene todos los objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> y `InspectorWrapper` que administra el complemento de VSTO.  
  
   - El campo `inspectors` mantiene una referencia a la colección de ventanas de Inspector en la instancia actual de Outlook. Esta referencia impide que el recolector de elementos no usados libere la memoria que contiene el controlador de evento del evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> , que declarará en el paso siguiente.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3. Reemplace el método `ThisAddIn_Startup` por el código siguiente. Este código asocia un controlador de eventos al evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> y pasa cada objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> existente al controlador de eventos. Si el usuario carga el complemento de VSTO después de que Outlook está en ejecución, el complemento de VSTO usa esta información para crear paneles de tareas personalizados para todos los mensajes de correo electrónico que ya están abiertos.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4. Reemplace el método `ThisAddIn_ShutDown` por el código siguiente. Este código desasocia el controlador de eventos <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> y limpia los objetos usados por el complemento de VSTO.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5. Agregue el siguiente controlador de eventos <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a la clase `ThisAddIn` . Si un nuevo <xref:Microsoft.Office.Interop.Outlook.Inspector> contiene un mensaje de correo electrónico, el método crea una instancia de un nuevo `InspectorWrapper` objeto para administrar la relación entre el mensaje de correo electrónico y el panel de tareas correspondiente.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6. Agregue la siguiente propiedad a la clase `ThisAddIn` . Esta propiedad expone el campo `inspectorWrappersValue` privado al código que está fuera de la clase `ThisAddIn` .  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Punto de control  
 Compile el proyecto para asegurarse de que se compila sin errores.  
  
### <a name="to-build-your-project"></a>Para compilar el proyecto  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **OutlookMailItemTaskPane** y luego haga clic en **Compilar**. Compruebe que el proyecto se compila sin errores.  
  
## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Sincronizar el botón de alternancia de la cinta de opciones con el panel de tareas personalizado  
 Cuando el panel de tareas esté visible, el botón de alternancia aparecerá presionado y cuando el panel de tareas esté oculto, aparecerá sin presionar. Para sincronizar el estado del botón con el panel de tareas personalizado, modifique el controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia.  
  
### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Para sincronizar el panel de tareas personalizado con el botón de alternancia  
  
1.  En el diseñador de la cinta de opciones, haga doble clic en el botón de alternancia **Mostrar panel de tareas** .  
  
     Visual Studio genera automáticamente un controlador de eventos denominado `toggleButton1_Click`, que controla el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Visual Studio también abre el archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* en el Editor de código.  
  
2.  Agregue las instrucciones siguientes al comienzo del archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* .  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Reemplace el controlador de eventos `toggleButton1_Click` por el siguiente código: Cuando el usuario hace clic en el botón de alternancia, este método muestra u oculta el panel de tareas personalizado que está asociado a la ventana de inspector actual.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="test-the-project"></a>El proyecto de prueba  
 Cuando empiece a depurar el proyecto, Outlook se abrirá y se cargará el complemento de VSTO. El complemento de VSTO muestra una única instancia del panel de tareas personalizado con cada mensaje de correo electrónico que se abre. Cree varios mensajes de correo electrónico nuevo para probar el código.  
  
### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento de VSTO  
  
1. Presione **F5**.  
  
2. En Outlook, haga clic en **New** para crear un nuevo mensaje de correo electrónico.  
  
3. En la cinta de opciones de mensaje de correo electrónico, haga clic en el **Add-Ins** pestaña y, a continuación, haga clic en el **Mostrar panel de tareas** botón.  
  
    Compruebe que un panel de tareas con el título **Mi panel de tareas** se muestra con el mensaje de correo electrónico.  
  
4. En el panel de tareas, escriba **Primer panel de tareas** en el cuadro de texto.  
  
5. Cierre el panel de tareas.  
  
    Compruebe que el estado del botón **Mostrar panel de tareas** cambia y ya no aparece presionado.  
  
6. Haga clic en el botón **Mostrar panel de tareas** de nuevo.  
  
    Compruebe que se abre el panel de tareas y que el cuadro de texto todavía contiene la cadena **Primer panel de tareas**.  
  
7. En Outlook, haga clic en **New** para crear un segundo mensaje de correo electrónico.  
  
8. En la cinta de opciones de mensaje de correo electrónico, haga clic en el **Add-Ins** pestaña y, a continuación, haga clic en el **Mostrar panel de tareas** botón.  
  
    Compruebe que un panel de tareas con el título **Mi panel de tareas** se muestra con el mensaje de correo electrónico, y el cuadro de texto en el panel de tareas está vacío.  
  
9. En el panel de tareas, escriba **Segundo panel de tareas** en el cuadro de texto.  
  
10. Cambiar el foco al primer mensaje de correo electrónico.  
  
     Compruebe que el panel de tareas que está asociado a este mensaje de correo electrónico aún aparece **primer panel de tareas** en el cuadro de texto.  
  
    Este complemento de VSTO también administra escenarios más avanzados que puede probar. Por ejemplo, puede probar el comportamiento cuando se ven mensajes de correo electrónico mediante el uso de la **siguiente elemento** y **anterior elemento** botones. También puede probar el comportamiento al descargar el complemento de VSTO, abrir varios mensajes de correo electrónico y, a continuación, vuelva a cargar el complemento de VSTO.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede obtener más información sobre cómo crear paneles de tareas personalizados en estos temas:  
  
-   Crear un panel de tareas personalizado en un complemento de VSTO para una aplicación diferente. Para obtener más información acerca de las aplicaciones que admiten paneles de tareas personalizados, vea [paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
-   Automatizar una aplicación de Microsoft Office mediante un panel de tareas personalizado. Para obtener más información, consulte [Tutorial: automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Crear un botón de cinta de opciones en Excel que se puede usar para ocultar o mostrar un panel de tareas personalizado. Para obtener más información, consulte [Tutorial: sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>Vea también  
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  