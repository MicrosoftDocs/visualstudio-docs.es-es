---
title: Paneles de tareas personalizados
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3bb4f99c4a77a398cb1f5e3765ee6353a367fb7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923158"
---
# <a name="custom-task-panes"></a>Paneles de tareas personalizados
  Los paneles de tareas son paneles de interfaz de usuario que normalmente están acoplados a un lado de una ventana en una aplicación de Microsoft Office. Los paneles de tareas personalizados proporcionan una manera de crear su propio panel de tareas y ofrecer a los usuarios una interfaz conocida para acceder a las características de la solución. Por ejemplo, la interfaz puede contener controles que ejecutan código para modificar documentos o mostrar datos de un origen de datos.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Un panel de tareas personalizado difiere del panel de acciones. El panel de acciones es parte de las personalizaciones de nivel de documento de Microsoft Office Word y Microsoft Office Excel. Para obtener más información, consulte [información general sobre el panel de acciones](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Ventajas de los paneles de tareas personalizados  
 Los paneles de tareas personalizados permiten integrar características en una interfaz de usuario conocida. Puede crear un panel de tareas personalizado rápidamente con herramientas de Visual Studio.  
  
### <a name="familiar-user-interface"></a>Interfaz de usuario conocida  
 Los usuarios de aplicaciones de Microsoft Office system ya están familiarizados con el uso de paneles de tareas, como el **estilos y formato** panel de tareas en Word. Los paneles de tareas personalizados se comportan como los demás paneles de tareas de Microsoft Office System. Los usuarios pueden acoplar paneles de tareas personalizados en diferentes lados de la ventana de la aplicación o pueden arrastrar paneles de tareas personalizados a cualquier lugar de la ventana. Puede crear un complemento de VSTO que muestre varios paneles de tareas personalizados al mismo tiempo, y los usuarios pueden controlar cada panel de tareas individualmente.  
  
### <a name="windows-forms-support"></a>Compatibilidad con formularios Windows forms  
 La interfaz de usuario de un panel de tareas personalizado que se crea con las herramientas de desarrollo de Office en Visual Studio se basa en controles de Windows Forms. Puede usar el ya conocido Diseñador de Windows Forms para diseñar la interfaz de usuario de un panel de tareas personalizado. También puede usar la compatibilidad de enlace de datos de Windows Forms para enlazar un origen de datos a controles del panel de tareas.  
  
## <a name="create-a-custom-task-pane"></a>Crear un panel de tareas personalizado  
 Puede crear un panel de tareas personalizado básico en dos pasos:  
  
1. Cree una interfaz de usuario para el panel de tareas personalizado agregando controles de Windows Forms al objeto <xref:System.Windows.Forms.UserControl>.  
  
2. Cree una instancia del panel de tareas personalizado pasando el control de usuario al objeto <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> en su complemento de VSTO. Esta colección devuelve un nuevo objeto <xref:Microsoft.Office.Tools.CustomTaskPane> que puede usar para modificar el aspecto del panel de tareas y responder a eventos de usuario.  
  
   Para obtener más información, vea [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="create-the-user-interface"></a>Crear la interfaz de usuario  
 Todos los paneles de tareas personalizados que se crean con las herramientas de desarrollo de Office en Visual Studio contienen un objeto <xref:System.Windows.Forms.UserControl>. Este control de usuario proporciona la interfaz de usuario de su panel de tareas personalizado. Puede crear el control de usuario en tiempo de diseño o en tiempo de ejecución. Si crea el control de usuario en tiempo de diseño, puede usar el Diseñador de Windows Forms para construir la interfaz de usuario de su panel de tareas.  
  
### <a name="instantiate-the-custom-task-pane"></a>Crear una instancia del panel de tareas personalizado  
 Después de crear un control de usuario que contenga la interfaz de usuario del panel de tareas personalizado, debe crear una instancia de <xref:Microsoft.Office.Tools.CustomTaskPane>. Para ello, pase el control de usuario a <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> en el complemento de VSTO llamando a uno de los métodos <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>. Esta colección se expone como el campo `CustomTaskPanes` de la clase `ThisAddIn`. El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisAddIn`.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 Los métodos <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> devuelven un nuevo objeto <xref:Microsoft.Office.Tools.CustomTaskPane>. Puede usar este objeto para modificar el aspecto del panel de tareas y responder a eventos de usuario.  
  
### <a name="control-the-task-pane-in-multiple-windows"></a>El panel de tareas en varias ventanas de control  
 Los paneles de tareas personalizados están asociados a una ventana de marco de documento, que presenta al usuario una vista de un documento o elemento. El panel de tareas solo está visible cuando la ventana asociada está visible.  
  
 Para determinar qué ventana muestra el panel de tareas personalizado, use la sobrecarga del método <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> adecuada al crear el panel de tareas:  
  
- Para asociar el panel de tareas a la ventana activa, use el método <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
- Para asociar el panel de tareas a un documento que se hospeda en una ventana especificada, use el método <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>.  
  
  Algunas aplicaciones de Office requieren instrucciones explícitas acerca de cuándo crear o mostrar el panel de tareas cuando se abre más de una ventana. Esto hace que sea más importante tener en cuenta dónde se crean las instancias de un panel de tareas personalizado en el código, para asegurarse de que el panel de tareas aparece con los documentos o elementos adecuados en la aplicación. Para obtener más información, consulte [administrar paneles de tareas personalizados en las ventanas de la aplicación](#Managing).  
  
## <a name="access-the-application-from-the-task-pane"></a>Acceso a la aplicación desde el panel de tareas  
 Si desea automatizar la aplicación desde el control de usuario, puede acceder directamente al modelo de objetos usando `Globals.ThisAddIn.Application` en el código. La clase `Globals` estática proporciona acceso al objeto `ThisAddIn`. El campo `Application` de este objeto es el punto de entrada al modelo de objetos de la aplicación.  
  
 Para obtener más información sobre la `Application` campo de la `ThisAddIn` de objetos, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md). Para ver un tutorial que muestra cómo automatizar una aplicación desde un panel de tareas personalizado, vea [Tutorial: Operación automática de una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Para obtener más información sobre la `Globals` de clases, vea [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="manage-the-user-interface-of-the-task-pane"></a>Administrar la interfaz de usuario del panel de tareas  
 Después de crear el panel de tareas, puede usar las propiedades y los eventos del objeto <xref:Microsoft.Office.Tools.CustomTaskPane> para controlar la interfaz de usuario del panel de tareas y responder cuando el usuario cambia el panel de tareas.  
  
### <a name="make-the-custom-task-pane-visible"></a>Hacer visible el panel de tareas personalizado  
 De forma predeterminada, el panel de tareas no está visible. Para hacer visible el panel de tareas, debe establecer el <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> propiedad **true**.  
  
 Los usuarios pueden cerrar un panel de tareas en cualquier momento haciendo clic en el **cerrar** botón (X) en la esquina del panel de tareas. Sin embargo, no hay ninguna manera predeterminada para que los usuarios vuelvan a abrir el panel de tareas personalizado. Si un usuario cierra un panel de tareas personalizado, no podrá volver a ver el panel de tareas personalizado, a menos que le proporcione la manera de mostrarlo.  
  
 Si crea un panel de tareas personalizado en el complemento de VSTO, debe crear también un elemento de interfaz de usuario, como un botón, en el que los usuarios puedan hacer clic para mostrar u ocultar el panel de tareas personalizado. Si crea un panel de tareas personalizado en una aplicación de Microsoft Office que admite la personalización de la cinta de opciones, puede agregar un grupo de controles a la cinta con un botón que muestre u oculte el panel de tareas personalizado. Para ver un tutorial que muestra cómo hacerlo, consulte [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Si crea un panel de tareas personalizado en una aplicación de Microsoft Office que no admite la personalización de la cinta de opciones, puede agregar un <xref:Microsoft.Office.Core.CommandBarButton> que muestre u oculte el panel de tareas personalizado.  
  
### <a name="modify-the-appearance-of-the-task-pane"></a>Modificar la apariencia del panel de tareas  
 Puede controlar el tamaño y la ubicación de un panel de tareas personalizado mediante las propiedades del objeto <xref:Microsoft.Office.Tools.CustomTaskPane>. Puede realizar muchos otros cambios en el aspecto de un panel de tareas personalizado usando las propiedades del objeto <xref:System.Windows.Forms.UserControl> que se encuentra en el panel de tareas personalizado. Por ejemplo, puede especificar una imagen de fondo para un panel de tareas personalizado mediante la propiedad <xref:System.Windows.Forms.Control.BackgroundImage%2A> del control de usuario.  
  
 En la tabla siguiente se enumeran los cambios que puede realizar en un panel de tareas personalizado usando las propiedades <xref:Microsoft.Office.Tools.CustomTaskPane>.  
  
|Tarea|Property|  
|----------|--------------|  
|Para cambiar el tamaño del panel de tareas|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Para cambiar la ubicación del panel de tareas|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Para ocultar el panel de tareas o hacerlo visible|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Para evitar que el usuario cambie la ubicación del panel de tareas|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="program-custom-task-pane-events"></a>Programar eventos del panel de tareas personalizado  
 Tal vez desee que el complemento de VSTO responda cuando el usuario modifique el panel de tareas personalizado. Por ejemplo, si el usuario cambia la orientación del panel de vertical a horizontal, quizás desee cambiar la posición de los controles.  
  
 En la tabla siguiente se enumeran los eventos que puede controlar para responder a los cambios que el usuario realice en el panel de tareas personalizado.  
  
|Tarea|evento|  
|----------|-----------|  
|Responder cuando el usuario cambia la ubicación del panel de tareas.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Responder cuando el usuario oculta el panel de tareas o lo hace visible.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="clean-up-resources-used-by-the-task-pane"></a>Limpiar los recursos utilizados por el panel de tareas  
 Después de crear un panel de tareas personalizado, el objeto <xref:Microsoft.Office.Tools.CustomTaskPane> permanece en memoria mientras se ejecuta el complemento de VSTO. El objeto permanece en memoria incluso después de que el usuario hace clic en el **cerrar** botón (X) en la esquina del panel de tareas.  
  
 Para limpiar los recursos que usa el panel de tareas mientras el complemento de VSTO se está ejecutando, use los métodos <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A>. Estos métodos quitan el objeto <xref:Microsoft.Office.Tools.CustomTaskPane> especificado de la colección `CustomTaskPanes` y llaman al método <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> del objeto.  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] limpia automáticamente los recursos que usa el panel de tareas personalizado cuando se descarga el complemento de VSTO. No llame a la <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> o <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> métodos en el `ThisAddIn_Shutdown` controlador de eventos en el proyecto. Estos métodos producirán <xref:System.ObjectDisposedException>, ya que [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] limpia los recursos que usa el objeto <xref:Microsoft.Office.Tools.CustomTaskPane> antes de llamar a `ThisAddIn_Shutdown`. Para obtener más información acerca de `ThisAddIn_Shutdown`, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Administrar paneles de tareas personalizados en varias ventanas de aplicación  
 Cuando se crea un panel de tareas personalizado en una aplicación que usa varias ventanas para mostrar documentos y otros elementos, deberá llevar a cabo otros pasos para asegurarse de que el panel de tareas está visible cuando el usuario así lo espere.  
  
 Los paneles de tareas personalizados de todas las aplicaciones están asociados a una ventana de marco de documento, que presenta al usuario una vista de un documento o elemento. El panel de tareas solo está visible cuando la ventana asociada está visible. Sin embargo, no todas las aplicaciones usan ventanas de marco de documento de la misma forma.  
  
 Los grupos de aplicaciones siguientes tienen requisitos de desarrollo diferentes:  
  
- [Outlook](#Outlook)  
  
- [Word, InfoPath y PowerPoint](#WordAndInfoPath)  
  
  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Administrar paneles de tareas en complementos de VSTO de Word? ](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Outlook  
 Cuando se crea un panel de tareas personalizado para Outlook, se asocia a una ventana específica del Explorador o el Inspector. Los exploradores son ventanas que muestran el contenido de una carpeta y los inspectores son ventanas que muestran un elemento como un mensaje de correo electrónico o una tarea.  
  
 Si desea mostrar un panel de tareas personalizado con varias ventanas del Explorador o el Inspector, deberá crear una nueva instancia del panel de tareas personalizado cuando se abre una ventana del Explorador o el Inspector. Para ello, controle el evento que se desencadena al crear una ventana del Explorador o el Inspector y, a continuación, cree el panel de tareas en el controlador de eventos. También puede administrar eventos del Explorador y del Inspector para ocultar o mostrar paneles de tareas, en función de qué ventana esté visible.  
  
 Para asociar el panel de tareas con un explorador o Inspector específico, use el <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método para crear el panel de tareas y pase el <xref:Microsoft.Office.Interop.Outlook.Explorer> o <xref:Microsoft.Office.Interop.Outlook.Inspector> de objeto para el *ventana* parámetro. Para obtener más información sobre la creación de paneles de tareas personalizados, vea [información general de paneles de tareas personalizado](../vsto/custom-task-panes.md).  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
  Para supervisar el estado de las ventanas del Inspector, puede administrar los siguientes eventos relacionados con el Inspector:  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Evitar que varias instancias de un panel de tareas personalizado en Outlook  
 Para evitar que las ventanas de Outlook muestren varias instancias de un panel de tareas personalizado, quite explícitamente el panel de tareas personalizado de la colección `CustomTaskPanes` de la clase `ThisAddIn` cuando se cierra cada ventana. Llame al método <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> en un evento que se desencadene al cerrar una ventana, como <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> o <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Si no quita explícitamente el panel de tareas personalizado, las ventanas de Outlook podrían mostrar varias instancias del panel de tareas personalizado. En ocasiones Outlook recicla las ventanas, y las ventanas recicladas conservan referencias a los paneles de tareas personalizados que se les adjuntaron.  
  
##  <a name="WordAndInfoPath"></a> Word, InfoPath y PowerPoint  
 Word, InfoPath y PowerPoint muestran cada documento en una ventana de marco de documento diferente. Cuando se crea un panel de tareas personalizado para estas aplicaciones, el panel se asocia únicamente a un documento específico. Si el usuario abre un documento diferente, el panel de tareas personalizado se oculta hasta que el documento anterior esté visible de nuevo.  
  
 Si desea mostrar un panel de tareas personalizado con varios documentos, cree una nueva instancia del panel de tareas personalizado cuando el usuario cree un documento nuevo o abra un documento existente. Para ello, controle los eventos que se generan cuando se crea o se abre un documento y, a continuación, cree el panel de tareas en los controladores de eventos. También puede administrar eventos del documento para ocultar o mostrar paneles de tareas, en función de qué documento esté visible.  
  
 Para asociar el panel de tareas con una ventana de documento específico, use el <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> método para crear el panel de tareas y pase un <xref:Microsoft.Office.Interop.Word.Window> (para Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (para InfoPath) o <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (para PowerPoint) a la *ventana*parámetro.  
  
### <a name="word-events"></a>Eventos de Word  
 Para supervisar el estado de las ventanas de documento en Word, puede administrar los eventos siguientes:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Eventos de InfoPath  
 Para supervisar el estado de las ventanas de documento en InfoPath, puede administrar los eventos siguientes:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Eventos de PowerPoint  
 Para supervisar el estado de las ventanas de documento en PowerPoint, puede administrar los eventos siguientes:  
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14)) 
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))
  
## <a name="see-also"></a>Vea también  
 [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
