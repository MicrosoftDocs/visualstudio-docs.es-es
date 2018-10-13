---
title: Enlazar controles WPF a WCF data Services | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdd13647eb485fa20da9c95a1c67ccc3e5f38cc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251841"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Enlazar controles de WPF a un servicio de datos de WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En este tutorial, se creará una aplicación de WPF que contiene controles enlazados a datos. Los controles se enlazan a registros de clientes que se encapsulan en un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. También agregará botones que los clientes pueden usar para ver y actualizar los registros.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un Entity Data Model que se genera a partir de los datos de la base de datos de ejemplo AdventureWorksLT.  
  
-   Creación de un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] que expone los datos de Entity Data Model a una aplicación WPF.  
  
-   Creación de un conjunto de controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta WPF designer.  
  
-   Crear botones que naveguen hacia adelante y hacia atrás por los registros de clientes.  
  
-   Creación de un botón que guarde los cambios a los datos de los controles a la [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] y el origen de datos subyacente.  
  
     [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
-   Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:  
  
-   Data Services de WCF. Para obtener más información, consulte [Introducción](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
-   Modelos de datos en [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].  
  
-   Entity Data Model y ADO.NET Entity Framework. Para obtener más información, consulte [Introducción a Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
-   Trabajar con WPF Designer. Para obtener más información, consulte [WPF y Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Enlace a datos de WPF. Para obtener más información, consulte [Información general sobre el enlace de datos](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-service-project"></a>Crear el proyecto de servicio  
 Para comenzar este tutorial, cree un proyecto para un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
#### <a name="to-create-the-service-project"></a>Para crear el proyecto de servicio  
  
1.  Inicie Visual Studio.  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  Expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Web**.  
  
4.  Seleccione la plantilla de proyecto **Aplicación web ASP.NET**.  
  
5.  En el **nombre** , escriba `AdventureWorksService` y haga clic en **Aceptar**.  
  
     Visual Studio crea el `AdventureWorksService` proyecto.  
  
6.  En **el Explorador de soluciones**, haga clic en **Default.aspx** y seleccione **eliminar**. Este archivo no es necesario en este tutorial.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Crear un Entity Data Model para el servicio  
 Para exponer datos a una aplicación usando un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], debe definir un modelo de datos para el servicio. El [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] admite dos tipos de modelos de datos: Entity Data Model y modelos de datos personalizados que se definen mediante objetos de common language runtime (CLR) que implementan la <xref:System.Linq.IQueryable%601> interfaz. En este tutorial, se crea un Entity Data Model para el modelo de datos.  
  
#### <a name="to-create-an-entity-data-model"></a>Para crear un Entity Data Model  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  En la lista de plantillas instaladas, haga clic en **datos**y, a continuación, seleccione el **ADO.NET Entity Data Model** elemento de proyecto.  
  
3.  Cambie el nombre a `AdventureWorksModel.edmx`y haga clic en **agregar**.  
  
     El **Entity Data Model**abre el asistente.  
  
4.  En el **Elegir contenido de Model** página, haga clic en **generar desde la base de datos**y haga clic en **siguiente**.  
  
5.  En el **elegir la conexión de datos** página, seleccione una de las siguientes opciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.  
  
    -   Haga clic en **nueva conexión**y crear una conexión a la base de datos AdventureWorksLT.  
  
6.  En el **elegir la conexión de datos** página, asegúrese de que el **Guardar configuración de conexión de entidad en App.Config como** opción está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7.  En el **elija los objetos de base de datos** , expanda **tablas**y, a continuación, seleccione el **SalesOrderHeader** tabla.  
  
8.  Haga clic en **Finalizar**.  
  
## <a name="create-the-service"></a>Crear el servicio  
 Crear un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] para exponer los datos de Entity Data Model a una aplicación WPF.  
  
#### <a name="to-create-the-service"></a>Para crear el servicio  
  
1.  En el **proyecto** menú, seleccione **Agregar nuevo elemento**.  
  
2.  En la lista de plantillas instaladas, haga clic en **Web**y, a continuación, seleccione el **WCF Data Service** elemento de proyecto.  
  
3.  En el **nombre** , escriba `AdventureWorksService.svc`y haga clic en **agregar**.  
  
     Visual Studio agrega el `AdventureWorksService.svc` al proyecto.  
  
## <a name="configure-the-service"></a>Configure el servicio  
 Debe configurar el servicio para trabajar con el Entity Data Model que ha creado.  
  
#### <a name="to-configure-the-service"></a>Para configurar el servicio  
  
1.  En el `AdventureWorks.svc` archivo de código, reemplace el `AdventureWorksService` declaración con el siguiente código de la clase.  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     Este código actualiza el `AdventureWorksService` clase, por lo que se derive de una <xref:System.Data.Services.DataService%601> que opera el `AdventureWorksLTEntities` objeto de clase de contexto en el Entity Data Model. También actualiza el método `InitializeService` para que los clientes del servicio tengan acceso completo de lectura y escritura a la entidad `SalesOrderHeader`.  
  
2.  Compile el proyecto y compruebe que se compila sin errores.  
  
## <a name="create-the-wpf-client-application"></a>Crear la aplicación cliente WPF  
 Para mostrar los datos del [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], cree una nueva aplicación de WPF con un origen de datos basado en el servicio. Más adelante en este procedimiento, agregará controles enlazados a datos a la aplicación.  
  
#### <a name="to-create-the-wpf-client-application"></a>Para crear la aplicación cliente de WPF  
  
1.  En **el Explorador de soluciones**, haga clic en el nodo de soluciones, haga clic en **agregar**y seleccione **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic**y, a continuación, seleccione **Windows**.  
  
3.  Seleccione el **aplicación WPF** plantilla de proyecto.  
  
4.  En el **nombre** , escriba `AdventureWorksSalesEditor`y haga clic en **Aceptar**.  
  
     Visual Studio agrega el `AdventureWorksSalesEditor` proyecto a la solución.  
  
5.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
     El **orígenes de datos** abre la ventana.  
  
6.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
     El **configuración origen de datos**abre el asistente.  
  
7.  En el **elegir un tipo de origen de datos** página del asistente, seleccione **servicio**y, a continuación, haga clic en **siguiente**.  
  
8.  En el **Add Service Reference** cuadro de diálogo, haga clic en **Discover**.  
  
     Visual Studio busca en la solución actual para los servicios disponibles y agrega `AdventureWorksService.svc` a la lista de servicios disponibles en el **servicios** cuadro.  
  
9. En el **Namespace** , escriba `AdventureWorksService`.  
  
10. En el **servicios** cuadro, haga clic en **AdventureWorksService.svc**y, a continuación, haga clic en **Aceptar**.  
  
     Visual Studio descarga la información de servicio y, a continuación, se devuelve a la **configuración origen de datos** asistente.  
  
11. En el **Add Service Reference** página, haga clic en **finalizar**.  
  
     Visual Studio agrega los nodos que representan los datos devueltos por el servicio para el **orígenes de datos** ventana.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definir la interfaz de usuario de la ventana  
 Agregue varios botones a la ventana modificando el código XAML en WPF Designer. Más adelante en este tutorial, agregará código que permite a los usuarios ver y actualizar los registros de ventas usando estos botones.  
  
#### <a name="to-create-the-window-layout"></a>Para crear el diseño de la ventana  
  
1.  En **el Explorador de soluciones**, haga doble clic en MainWindow.xaml.  
  
     La ventana se abre en WPF Designer.  
  
2.  En la vista [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] del diseñador, agregue el código siguiente entre las etiquetas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compile el proyecto.  
  
## <a name="create-the-data-bound-controls"></a>Crear los controles enlazados a datos  
 Crear controles que muestren registros de clientes, arrastrando el `SalesOrderHeaders` nodo desde el **orígenes de datos** ventana al diseñador.  
  
#### <a name="to-create-the-data-bound-controls"></a>Para crear controles enlazados a datos  
  
1.  En el **orígenes de datos** ventana, haga clic en el menú desplegable de la **SalesOrderHeaders** nodo y seleccione **detalles**.  
  
2.  Expanda el **SalesOrderHeaders** nodo.  
  
3.  En este ejemplo, algunos campos no se mostrarán, así que haga clic en el menú desplegable junto a los nodos siguientes y seleccione **ninguno**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Esta acción impide que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente. En este tutorial, se supone que el usuario final no necesita ver estos datos.  
  
4.  Desde el **orígenes de datos** ventana, arrastre el **SalesOrderHeaders** nodo a la fila de cuadrícula debajo de la fila que contiene los botones.  
  
     Visual Studio genera XAML y código que crea un conjunto de controles que están enlazados a datos en el **producto** tabla. Para obtener más información sobre el XAML y el código generado, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  En el diseñador, haga clic en el cuadro de texto junto a la **Id. de cliente** etiqueta.  
  
6.  En el **propiedades** ventana, seleccione la casilla de verificación junto a la **IsReadOnly** propiedad.  
  
7.  Establecer el **IsReadOnly** propiedad para cada uno de los cuadros de texto siguientes:  
  
    -   **Número de pedido de compra**  
  
    -   **Id. de pedido de ventas**  
  
    -   **Número de pedido de ventas**  
  
## <a name="load-the-data-from-the-service"></a>Cargar los datos desde el servicio  
 Utilice el objeto de proxy de servicio para cargar los datos de ventas desde el servicio. A continuación, asigne los datos devueltos al origen de datos para el <xref:System.Windows.Data.CollectionViewSource> en la ventana de WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>Para cargar los datos del servicio  
  
1.  En el diseñador, para crear el `Window_Loaded` controlador de eventos, haga doble clic en el texto que dice: **MainWindow**.  
  
2.  Reemplace el controlador de evento con el código siguiente: Asegúrese de que reemplaza el *localhost* dirección en este código con la dirección de host local en el equipo de desarrollo.  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Registros de Navigatesales  
 Agregue código que permita a los usuarios desplazarse por los registros de ventas usando el **\<** y **>** botones.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Para que los usuarios puedan navegar por los registros de ventas  
  
1.  En el diseñador, haga doble clic en el **<** botón en la superficie de la ventana.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo `backButton_Click` controlador de eventos para el <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
2.  Agregue el código siguiente al controlador de evento `backButton_Click` generado:  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3.  Vuelva al diseñador y haga doble clic en el **>** botón.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo `nextButton_Click` controlador de eventos para el <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
4.  Agregue el código siguiente al controlador de evento `nextButton_Click` generado:  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>Guardando los cambios en los registros de ventas  
 Agregue código que permita a los usuarios ver y guardar los cambios en los registros de ventas mediante la **guardar cambios** botón.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Para agregar la posibilidad de guardar cambios en los registros de ventas  
  
1.  En el diseñador, haga doble clic en el **guardar cambios** botón.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo `saveButton_Click` controlador de eventos para el <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
2.  Agregue el código siguiente al controlador de eventos `saveButton_Click`.  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Compile y ejecute la aplicación para comprobar que puede ver y actualizar los registros de clientes.  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  En **compilar** menú, haga clic en **compilar solución**. Compruebe que la solución se compila sin errores.  
  
2.  Presione **Ctrl + F5**.  
  
     Visual Studio inicia el **AdventureWorksService** proyecto sin depurarlo.  
  
3.  En **el Explorador de soluciones**, haga clic en el **AdventureWorksSalesEditor** proyecto.  
  
4.  En el menú contextual, en **depurar**, haga clic en **Iniciar nueva instancia**.  
  
     La aplicación se ejecuta. Compruebe lo siguiente:  
  
    -   Los cuadros de texto muestran distintos campos de datos desde el primer registro de ventas, que tiene el identificador de pedido de ventas **71774**.  
  
    -   Puede hacer clic en el **>** o **<** botones para navegar por otros registros de ventas.  
  
5.  En uno de los registros de ventas, escriba algún texto en el **comentario** cuadro y, a continuación, haga clic en **guardar cambios**.  
  
6.  Cierre la aplicación y vuelva a iniciarla en Visual Studio.  
  
7.  Vaya al registro de ventas que ha cambiado y compruebe que el cambio se conserva después de cerrar y volver a abrir la aplicación.  
  
8.  Cierre la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Una vez completado este tutorial, puede realizar las siguientes tareas relacionadas:  
  
-   Aprenda a usar el **orígenes de datos** controla la ventana de Visual Studio para enlazar WPF a otros tipos de orígenes de datos. Para obtener más información, consulte [WPF enlazar controles a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Aprenda a usar el **orígenes de datos** ventana de Visual Studio para mostrar datos relacionados (es decir, los datos en una relación de elementos primarios y secundarios) en los controles de WPF. Para obtener más información, consulte [Tutorial: mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Información general](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Introducción a Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [Información general de diseñador de Silverlight y WPF](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Información general sobre el enlace de datos](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

