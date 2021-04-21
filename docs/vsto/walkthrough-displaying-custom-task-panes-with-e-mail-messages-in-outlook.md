---
title: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook
description: Obtenga información sobre cómo mostrar una instancia única de un panel de tareas personalizado con cada mensaje de correo electrónico en Microsoft Outlook que se crea o abre.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bb1aed5ef110b726dae6e51337b0934ae0a8e69d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824216"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook
  En este tutorial se muestra cómo mostrar una instancia única de un panel de tareas personalizado con cada mensaje de correo electrónico que se crea o se abre. Los usuarios pueden mostrar u ocultar el panel de tareas personalizado mediante un botón de la cinta de opciones de cada mensaje de correo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Para mostrar un panel de tareas personalizado con varias ventanas de explorador o inspector, es necesario crear una instancia del panel de tareas personalizado para cada ventana que se abra. Para obtener más información sobre el comportamiento de los paneles de tareas personalizados en ventanas de Outlook, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md).

> [!NOTE]
> En este tutorial se presenta el código del complemento de VSTO en pequeñas secciones para que resulte más fácil explicar la lógica detrás del código.

 En este tutorial se muestran las tareas siguientes:

- Diseñar la interfaz de usuario (UI) del panel de tareas personalizado.

- Crear una interfaz de usuario de cinta de opciones personalizada.

- Mostrar la interfaz de usuario personalizada de la cinta de opciones con mensajes de correo electrónico.

- Crear una clase para administrar ventanas de inspector y paneles de tareas personalizados.

- Inicializar y limpiar los recursos usados por el complemento de VSTO.

- Sincronizar el botón de alternancia de la cinta de opciones con el panel de tareas personalizado.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o Microsoft Outlook 2010.

## <a name="create-the-project"></a>Creación del proyecto
 Los paneles de tareas personalizados se implementan en complementos de VSTO. Empiece por crear un proyecto de complemento de VSTO para Outlook.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Crear un proyecto **Complemento de Outlook** con el nombre **OutlookMailItemTaskPane**. Use la plantilla de proyecto **Complemento de Outlook** . Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código *ThisAddIn.cs* o *ThisAddIn.vb* y agrega el proyecto **OutlookMailItemTaskPane** al **Explorador de soluciones**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Diseño de la interfaz de usuario del panel de tareas personalizado
 No hay ningún diseñador visual para los paneles de tareas personalizados, pero puede diseñar un control de usuario con la interfaz de usuario que desee. El panel de tareas personalizado de este complemento de VSTO tiene una interfaz de usuario simple que contiene un control <xref:System.Windows.Forms.TextBox> . Más adelante en este tutorial, agregará el control de usuario al panel de tareas personalizado.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Para diseñar la interfaz de usuario del panel de tareas personalizado

1. En el **Explorador de soluciones**, haga clic en el proyecto **OutlookMailItemTaskPane** .

2. En el menú **Proyecto** , haga clic en **Agregar control de usuario**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , cambie el nombre del control de usuario a **TaskPaneControl** y haga clic en **Agregar**.

     Se abre el control de usuario en el diseñador.

4. En la pestaña **Controles comunes** del **Cuadro de herramientas**, arrastre un control **TextBox** hasta el control de usuario.

## <a name="design-the-user-interface-of-the-ribbon"></a>Diseño de la interfaz de usuario de la cinta de opciones
 Uno de los objetivos de este complemento de VSTO es proporcionar a los usuarios una manera de ocultar o mostrar el panel de tareas personalizado en la cinta de opciones de cada mensaje de correo electrónico. Para proporcionar la interfaz de usuario, cree una interfaz de usuario de cinta de opciones personalizada que muestre un botón de alternancia en el que los usuarios pueden hacer clic para mostrar u ocultar el panel de tareas personalizado.

### <a name="to-create-a-custom-ribbon-ui"></a>Para crear una interfaz de usuario de cinta de opciones personalizada

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)**.

3. Cambie el nombre de la nueva cinta de opciones por **ManageTaskPaneRibbon** y haga clic en **Agregar**.

     El archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* se abre en el diseñador de la cinta de opciones y muestra una pestaña y un grupo predeterminados.

4. En el diseñador de la cinta de opciones, haga clic en **group1** para seleccionarlo.

5. En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Administrador de panel de tareas**.

6. En la pestaña **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre un control ToggleButton al grupo **Administrador de panel de tareas** .

7. Haga clic en **toggleButton1**.

8. En la ventana **Propiedades** , establezca el valor de la propiedad **Label** en **Mostrar panel de tareas**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Mostrar la interfaz de usuario personalizada de la cinta de opciones con mensajes de correo electrónico
 El panel de tareas personalizado que va a crear en este tutorial se ha diseñado para que aparezca únicamente con las ventanas de inspector que contienen mensajes de correo. Por lo tanto, debe definir las propiedades de forma que la interfaz de usuario de la cinta de opciones personalizada solo aparezca con estas ventanas.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Para mostrar la interfaz de usuario personalizada de la cinta de opciones con mensajes de correo electrónico

1. En el diseñador de la cinta de opciones, haga clic en la cinta **ManageTaskPaneRibbon** .

2. En la ventana **Propiedades** , haga clic en la lista desplegable situada junto a **RibbonType** y seleccione **Microsoft.Outlook.Mail.Compose** y **Microsoft.Outlook.Mail.Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Creación de una clase para administrar ventanas de inspector y paneles de tareas personalizados
 Hay varios casos en los que el complemento de VSTO debe identificar qué panel de tareas personalizado está asociado a un mensaje de correo electrónico específico. Estos casos son los siguientes:

- Cuando el usuario cierra un mensaje de correo electrónico. En este caso, el complemento de VSTO debe quitar el panel de tareas personalizado correspondiente para garantizar que los recursos usados por el complemento de VSTO se limpian correctamente.

- Cuando el usuario cierra el panel de tareas personalizado. En este caso, el complemento de VSTO debe actualizar el estado del botón de alternancia en la cinta de opciones del mensaje de correo electrónico.

- Cuando el usuario hace clic en el botón de alternancia de la cinta de opciones. En este caso, el complemento de VSTO debe ocultar o mostrar el panel de tareas correspondiente.

  Para permitir que el complemento de VSTO realice un seguimiento de qué panel de tareas personalizado está asociado a cada mensaje de correo electrónico abierto, cree una clase personalizada que ajuste los pares de <xref:Microsoft.Office.Interop.Outlook.Inspector> objetos <xref:Microsoft.Office.Tools.CustomTaskPane> y . Esta clase crea un nuevo objeto de panel de tareas personalizado para cada mensaje de correo electrónico y elimina el panel de tareas personalizado cuando se cierra el mensaje de correo electrónico correspondiente.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Para crear una clase para administrar ventanas de inspector y paneles de tareas personalizados

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo *ThisAddIn.vb* o *ThisAddIn.cs* y luego haga clic en **Ver código**.

2. Agregue las instrucciones siguientes en la parte superior del archivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet2":::

3. Agregue el código siguiente al archivo *ThisAddIn.cs* o *ThisAddIn.vb* , fuera la clase `ThisAddIn` (para Visual C#, agregue este código dentro del espacio de nombres `OutlookMailItemTaskPane` ). La clase `InspectorWrapper` administra un par de objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> y <xref:Microsoft.Office.Tools.CustomTaskPane> . Completará la definición de esta clase en los pasos siguientes.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet3":::

4. Agregue el constructor siguiente después del código que agregó en el paso anterior. Este constructor crea e inicializa un nuevo panel de tareas personalizado que está asociado al objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que se pasa. En C#, el constructor asocia también controladores de eventos al evento <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> del objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> y al evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> del objeto <xref:Microsoft.Office.Tools.CustomTaskPane> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet4":::

5. Agregue el método siguiente después del código que agregó en el paso anterior. Este método es un controlador de eventos para el evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> de objeto <xref:Microsoft.Office.Tools.CustomTaskPane> que se encuentra en la clase `InspectorWrapper` . Este código actualiza el estado del botón de alternancia cada vez que el usuario abre o cierra el panel de tareas personalizado.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet5":::

6. Agregue el método siguiente después del código que agregó en el paso anterior. Este método es un controlador de eventos para el <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> evento del objeto que contiene el mensaje de correo electrónico <xref:Microsoft.Office.Interop.Outlook.Inspector> actual. El controlador de eventos libera recursos cuando se cierra el mensaje de correo electrónico. El controlador de eventos también quita el panel de tareas personalizado actual desde la colección `CustomTaskPanes` . Esto ayuda a evitar varias instancias del panel de tareas personalizado cuando se abre el siguiente mensaje de correo electrónico.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet6":::

7. Agregue el código siguiente después del código que agregó en el paso anterior. Más adelante en este tutorial, llamará a esta propiedad desde un método de la interfaz de usuario de la cinta de opciones para mostrar u ocultar el panel de tareas personalizado.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet7":::

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicialización y limpieza de los recursos usados por el complemento
 Agregue código a la clase `ThisAddIn` para inicializar el complemento de VSTO cuando este se cargue y para limpiar los recursos cuando dicho complemento se descargue. Para inicializar el complemento de VSTO, debe configurar un controlador de eventos para el evento y pasar todos los mensajes de correo electrónico existentes <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a este controlador de eventos. Una vez que se descargue el complemento de VSTO, desasocie el controlador de eventos y limpie los objetos utilizados por el complemento de VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Para inicializar y limpiar los recursos usados por el complemento de VSTO

1. En el archivo *ThisAddIn.cs* o *ThisAddIn.vb* , busque la definición de la clase `ThisAddIn` .

2. Agregue las declaraciones siguientes a la clase `ThisAddIn` :

   - El campo `inspectorWrappersValue` contiene todos los objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> y `InspectorWrapper` que administra el complemento de VSTO.

   - El campo `inspectors` mantiene una referencia a la colección de ventanas de Inspector en la instancia actual de Outlook. Esta referencia impide que el recolector de elementos no usados libere la memoria que contiene el controlador de evento del evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> , que declarará en el paso siguiente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet8":::

3. Reemplace el método `ThisAddIn_Startup` por el código siguiente. Este código asocia un controlador de eventos al evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> y pasa cada objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> existente al controlador de eventos. Si el usuario carga el complemento de VSTO una vez que Outlook ya se está ejecutando, el complemento de VSTO usa esta información para crear paneles de tareas personalizados para todos los mensajes de correo electrónico que ya están abiertos.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet9":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet9":::

4. Reemplace el método `ThisAddIn_ShutDown` por el código siguiente. Este código desasocia el controlador de eventos <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> y limpia los objetos usados por el complemento de VSTO.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet10":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet10":::

5. Agregue el siguiente controlador de eventos <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a la clase `ThisAddIn` . Si un nuevo contiene un mensaje de correo electrónico, el método crea una instancia de un nuevo objeto para administrar la relación entre el mensaje de correo electrónico y el <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` panel de tareas correspondiente.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet11":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet11":::

6. Agregue la siguiente propiedad a la clase `ThisAddIn` . Esta propiedad expone el campo `inspectorWrappersValue` privado al código que está fuera de la clase `ThisAddIn` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet12":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet12":::

## <a name="checkpoint"></a>Punto de control
 Compile el proyecto para asegurarse de que se compila sin errores.

### <a name="to-build-your-project"></a>Para compilar el proyecto

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **OutlookMailItemTaskPane** y luego haga clic en **Compilar**. Compruebe que el proyecto se compila sin errores.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Sincronizar el botón de alternancia de la cinta de opciones con el panel de tareas personalizado
 Cuando el panel de tareas esté visible, el botón de alternancia aparecerá presionado y cuando el panel de tareas esté oculto, aparecerá sin presionar. Para sincronizar el estado del botón con el panel de tareas personalizado, modifique el controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Para sincronizar el panel de tareas personalizado con el botón de alternancia

1. En el diseñador de la cinta de opciones, haga doble clic en el botón de alternancia **Mostrar panel de tareas** .

     Visual Studio genera automáticamente un controlador de eventos denominado `toggleButton1_Click`, que controla el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> del botón de alternancia. Visual Studio también abre el archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* en el Editor de código.

2. Agregue las instrucciones siguientes al comienzo del archivo *ManageTaskPaneRibbon.cs* o *ManageTaskPaneRibbon.vb* .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet14":::

3. Reemplace el controlador de eventos `toggleButton1_Click` por el siguiente código: Cuando el usuario hace clic en el botón de alternancia, este método muestra u oculta el panel de tareas personalizado que está asociado a la ventana de inspector actual.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet15":::

## <a name="test-the-project"></a>Prueba del proyecto
 Cuando empiece a depurar el proyecto, Outlook se abrirá y se cargará el complemento de VSTO. El complemento VSTO muestra una instancia única del panel de tareas personalizado con cada mensaje de correo electrónico que se abre. Cree varios mensajes de correo electrónico para probar el código.

### <a name="to-test-the-vsto-add-in"></a>Para probar el complemento de VSTO

1. Presione **F5**.

2. En Outlook, haga clic **en Nuevo** para crear un mensaje de correo electrónico.

3. En la cinta de opciones del mensaje de correo electrónico, haga clic en **la pestaña Complementos** y, a continuación, haga clic en el botón Mostrar panel **de** tareas.

    Compruebe que se muestra un panel de tareas con el título **Mi panel** de tareas con el mensaje de correo electrónico.

4. En el panel de tareas, escriba **Primer panel de tareas** en el cuadro de texto.

5. Cierre el panel de tareas.

    Compruebe que el estado del botón **Mostrar panel de tareas** cambia y ya no aparece presionado.

6. Haga clic en el botón **Mostrar panel de tareas** de nuevo.

    Compruebe que se abre el panel de tareas y que el cuadro de texto todavía contiene la cadena **Primer panel de tareas**.

7. En Outlook, haga clic **en Nuevo** para crear un segundo mensaje de correo electrónico.

8. En la cinta de opciones del mensaje de correo electrónico, haga clic en **la pestaña Complementos** y, a continuación, haga clic en el botón Mostrar panel **de** tareas.

    Compruebe que se muestra  un panel de tareas con el título Mi panel de tareas con el mensaje de correo electrónico y que el cuadro de texto de este panel de tareas está vacío.

9. En el panel de tareas, escriba **Segundo panel de tareas** en el cuadro de texto.

10. Cambie el foco al primer mensaje de correo electrónico.

     Compruebe que el panel de tareas asociado a este mensaje de correo electrónico todavía muestra **El primer panel de tareas** en el cuadro de texto.

    Este complemento de VSTO también administra escenarios más avanzados que puede probar. Por ejemplo, puede probar el comportamiento al ver correos electrónicos mediante los botones Siguiente **elemento** **y Elemento** anterior. También puede probar el comportamiento al descargar el complemento de VSTO, abrir varios mensajes de correo electrónico y, a continuación, volver a cargar el complemento de VSTO.

## <a name="next-steps"></a>Pasos siguientes
 En estos temas puede obtener más información sobre cómo crear paneles de tareas personalizados:

- Cree un panel de tareas personalizado en un complemento de VSTO para otra aplicación. Para obtener más información sobre las aplicaciones que admiten paneles de tareas personalizados, vea [Paneles de tareas personalizados.](../vsto/custom-task-panes.md)

- Automatizar una aplicación de Microsoft Office mediante un panel de tareas personalizado. Para obtener más información, [vea Tutorial: Automatización de una aplicación desde un panel de tareas personalizado.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)

- Crear un botón de cinta de opciones en Excel que se puede usar para ocultar o mostrar un panel de tareas personalizado. Para obtener más información, [vea Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>Consulte también
- [Paneles de tareas personalizados](../vsto/custom-task-panes.md)
- [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Tutorial: Automatización de una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Introducción al modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
