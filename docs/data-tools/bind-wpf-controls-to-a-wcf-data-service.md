---
title: "Tutorial: Enlazar controles de WPF a un servicio de datos de WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "enlace de datos de WPF [Visual Studio], tutoriales"
  - "WPF Designer, enlace de datos"
  - "WPF, enlace de datos en Visual Studio"
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Enlazar controles de WPF a un servicio de datos de WCF
En este tutorial, se creará una aplicación de WPF que contiene controles enlazados a datos.  Los controles se enlazan a registros de clientes que se encapsulan en un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  También agregará botones que los clientes pueden usar para ver y actualizar los registros.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un Entity Data Model que se genera a partir de los datos de la base de datos de ejemplo AdventureWorksLT.  
  
-   Crear un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que expone los datos del Entity Data Model a una aplicación de WPF.  
  
-   Crear un conjunto de controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta WPF Designer.  
  
-   Crear botones que naveguen hacia adelante y hacia atrás por los registros de clientes.  
  
-   Crear un botón que guarde los cambios a los datos de los controles en [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] y en el origen de datos subyacente.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT.  Puede descargar la base de datos AdventureWorksLT del [sitio web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:  
  
-   Servicios de datos de WCF.  Para obtener más información, vea [Información general](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Modelos de datos en [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
-   Entity Data Model y ADO.NET Entity Framework.  Para obtener más información, vea [Información general de Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Trabajar con WPF Designer.  Para obtener más información, vea [Información general sobre WPF y Silverlight Designer](http://msdn.microsoft.com/es-es/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Enlace a datos de WPF.  Para obtener más información, vea [Información general sobre el enlace de datos](../Topic/Data%20Binding%20Overview.md).  
  
## Crear el proyecto de servicio  
 Para comenzar este tutorial, cree un proyecto para un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
#### Para crear el proyecto de servicio  
  
1.  Inicie Visual Studio.  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  Expanda **Visual Basic** o **Visual C\#** y, después, seleccione **Web**.  
  
4.  Seleccione la plantilla de proyecto **Aplicación web ASP.NET**.  
  
5.  En el cuadro **Nombre**, escriba `AdventureWorksService` y haga clic en **Aceptar**.  
  
     Visual Studio crea el proyecto `AdventureWorksService`.  
  
6.  En el **Explorador de soluciones**, haga clic con el botón secundario en **Default.aspx** y seleccione **Eliminar**.  Este archivo no es necesario en este tutorial.  
  
## Crear un Entity Data Model para el servicio  
 Para exponer datos a una aplicación usando un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], debe definir un modelo de datos para el servicio.  El [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] admite dos tipos de modelos de datos: Entity Data Model y modelos de datos personalizados que se definen mediante objetos de Common Language Runtime \(CLR\) que implementan la interfaz <xref:System.Linq.IQueryable%601>.  En este tutorial, se crea un Entity Data Model para el modelo de datos.  
  
#### Para crear un Entity Data Model  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  En la lista Plantillas instaladas, haga clic en **Datos** y seleccione el elemento de proyecto **ADO.NET Entity Data Model**.  
  
3.  Cambie el nombre a `AdventureWorksModel.edmx` y haga clic en **Agregar**.  
  
     Se abre el **Asistente para Entity Data Model**.  
  
4.  En la página **Elegir contenido del modelo**, haga clic en **Generar desde la base de datos** y en **Siguiente**.  
  
5.  En la página **Elegir la conexión de datos**, seleccione una de estas opciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Haga clic en **Nueva conexión** y cree una conexión a la base de datos AdventureWorksLT.  
  
6.  En la página **Elegir la conexión de datos** asegúrese de que la opción **Guardar configuración de conexión de la entidad en App.Config como** está seleccionada y haga clic en **Siguiente**.  
  
7.  En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas** y seleccione la tabla **SalesOrderHeader**.  
  
8.  Haga clic en **Finalizar**.  
  
## Crear el servicio web  
 Cree un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] que expone los datos del Entity Data Model a una aplicación de WPF.  
  
#### Para crear el servicio  
  
1.  En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.  
  
2.  En la lista Plantillas instaladas, haga clic en **Web** y seleccione el elemento de proyecto **Servicio de datos de WCF**.  
  
3.  En el cuadro **Nombre**, escriba `AdventureWorksService.svc` y haga clic en **Agregar**.  
  
     Visual Studio agrega `AdventureWorksService.svc` al proyecto.  
  
## Configurar el servicio  
 Debe configurar el servicio para trabajar con el Entity Data Model que ha creado.  
  
#### Para configurar el servicio  
  
1.  En el archivo de código `AdventureWorks.svc`, reemplace la declaración de la clase `AdventureWorksService` por el código siguiente.  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     Este código actualiza la clase `AdventureWorksService` para que derive de un <xref:System.Data.Services.DataService%601> que trabaja con la clase de contexto de objeto `AdventureWorksLTEntities` en su Entity Data Model.  También actualiza el método `InitializeService` para que los clientes del servicio tengan acceso completo de lectura y escritura a la entidad `SalesOrderHeader`.  
  
2.  Compile el proyecto y compruebe que se compila sin errores.  
  
## Crear la aplicación cliente de WPF.  
 Para mostrar los datos del [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], cree una nueva aplicación de WPF con un origen de datos basado en el servicio.  Más adelante en este procedimiento, agregará controles enlazados a datos a la aplicación.  
  
#### Para crear la aplicación cliente de WPF  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, haga clic en **Agregar** y seleccione **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** o **Visual C\#** y, después, expanda **Windows**.  
  
3.  Seleccione la plantilla de proyecto **Aplicación WPF**.  
  
4.  En el cuadro **Nombre**, escriba `AdventureWorksSalesEditor` y haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto `AdventureWorksSalesEditor` a la solución.  
  
5.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
     Se abre la ventana **Orígenes de datos**.  
  
6.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos**.  
  
     Se abrirá el **Asistente para la configuración de orígenes de datos**.  
  
7.  En la página **Elija un tipo de origen de datos** del asistente, seleccione **Servicio** y haga clic en **Siguiente**.  
  
8.  En el cuadro de diálogo **Agregar referencia de servicio**, haga clic en **Detectar**.  
  
     Visual Studio busca los servicios disponibles en la solución actual y agrega `AdventureWorksService.svc` a la lista de servicios disponibles en el cuadro **Servicios**.  
  
9. En el cuadro **Espacio de nombres**, escriba `AdventureWorksService`.  
  
10. En el cuadro **Servicios**, haga clic en **AdventureWorksService.svc** y haga clic en **Aceptar**.  
  
     Visual Studio descarga la información del servicio y después vuelve al **Asistente para configuración de orígenes de datos**.  
  
11. En la página **Agregar referencia de servicio**, haga clic en **Finalizar**.  
  
     Visual Studio agrega los nodos que representan los datos devueltos por el servicio a la ventana **Orígenes de datos**.  
  
## Definir la interfaz de usuario de la ventana  
 Agregue varios botones a la ventana modificando el código XAML en WPF Designer.  Más adelante en este tutorial, agregará código que permite a los usuarios ver y actualizar los registros de ventas usando estos botones.  
  
#### Para crear el diseño de la ventana  
  
1.  En el **Explorador de soluciones**, haga doble clic en MainWindow.xaml.  
  
     La ventana se abre en WPF Designer.  
  
2.  En la vista [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] del diseñador, agregue el código siguiente entre las etiquetas `<Grid>`:  
  
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
  
## Crear los controles enlazados a datos  
 Cree controles que muestren registros de clientes, arrastrando el nodo `SalesOrderHeaders` desde la ventana **Orígenes de datos** hasta el diseñador.  
  
#### Para crear controles enlazados a datos  
  
1.  En la ventana **Orígenes de datos**, haga clic en el menú desplegable del nodo **SalesOrderHeaders** y seleccione **Detalles**.  
  
2.  Expanda el nodo **SalesOrderHeaders**.  
  
3.  En este ejemplo no se mostrarán algunos campos; por lo tanto, haga clic en el menú desplegable junto a los siguientes nodos y seleccione **Ninguno**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Esta acción impide que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente.  En este tutorial, se da por hecho que el usuario final no necesita ver estos datos.  
  
4.  Desde la ventana **Orígenes de datos**, arrastre el nodo **SalesOrderHeaders** a la fila de la cuadrícula situada debajo de la fila que contiene los botones.  
  
     Visual Studio genera el código XAML que crea un conjunto de controles que están enlazados a los datos de la tabla **Product**.  Para obtener más información sobre el código y el XAML generado, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  En el diseñador, haga clic en el cuadro de texto junto a la etiqueta **Customer ID**.  
  
6.  En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.  
  
7.  Establezca la propiedad **IsReadOnly** de cada uno de los cuadros de texto siguientes:  
  
    -   **Purchase Order Number**  
  
    -   **Sales Order ID**  
  
    -   **Sales Order Number**  
  
## Cargar los datos del servicio  
 Use el objeto proxy de servicio para cargar los datos de ventas del servicio y, después, asigne los datos devueltos al origen de datos para el <xref:System.Windows.Data.CollectionViewSource> en la ventana WPF.  
  
#### Para cargar los datos del servicio  
  
1.  En el diseñador, haga doble clic en el texto que dice: **MainWindow** para crear el controlador de evento `Window_Loaded`.  
  
2.  Reemplace el controlador de evento con el código siguiente:  Asegúrese de reemplazar la dirección *localhost* en este código por la dirección del host local de su equipo de desarrollo.  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## Navegar por los registros de ventas  
 Agregue código que permita a los usuarios desplazarse por los registros de ventas usando los botones **\<** y **\>**.  
  
#### Para que los usuarios puedan navegar por los registros de ventas  
  
1.  En el diseñador, haga doble clic en el botón **\<** en la superficie de la ventana.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `backButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Agregue el código siguiente al controlador de evento `backButton_Click` generado:  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  Vuelva al diseñador y haga doble clic en el botón **\>**.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `nextButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
4.  Agregue el código siguiente al controlador de evento `nextButton_Click` generado:  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## Guardar cambios en los registros de ventas  
 Agregue código que permita a los usuarios ver y guardar cambios en los registros de ventas usando el botón **Save changes**.  
  
#### Para agregar la posibilidad de guardar cambios en los registros de ventas  
  
1.  En el diseñador, haga doble clic en el botón **Save Changes**.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `saveButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Agregue el código siguiente al controlador de eventos `saveButton_Click`.  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## Probar la aplicación  
 Compile y ejecute la aplicación para comprobar que puede ver y actualizar los registros de clientes.  
  
#### Para probar la aplicación  
  
1.  En el menú **Compilar**, haga clic en **Compilar solución**.  Compruebe que la solución se compila sin errores.  
  
2.  Presione **CTRL\+F5**.  
  
     Visual Studio inicia el proyecto **AdventureWorksService** sin depurarlo.  
  
3.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **AdventureWorksSalesEditor**.  
  
4.  En el menú contextual, en **Depurar**, haga clic en **Iniciar nueva instancia**.  
  
     La aplicación se ejecuta.  Compruebe lo siguiente:  
  
    -   Los cuadros de texto muestran campos de datos diferentes de los del primer registro de ventas, que tiene el identificador de pedido de ventas **71774**.  
  
    -   Puede hacer clic en los botones **\>** o **\<** para navegar por otros registros de ventas.  
  
5.  En uno de los registros de ventas, escriba algún texto en el cuadro **Comment** y haga clic en **Save changes**.  
  
6.  Cierre la aplicación y vuelva a iniciarla en Visual Studio.  
  
7.  Vaya al registro de ventas que ha cambiado y compruebe que el cambio se conserva después de cerrar y volver a abrir la aplicación.  
  
8.  Cierre la aplicación.  
  
## Pasos siguientes  
 Una vez completado este tutorial, puede realizar las siguientes tareas relacionadas:  
  
-   Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para enlazar controles WPF a otros tipos de orígenes de datos.  Para obtener más información, vea [Tutorial: Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para mostrar datos relacionados \(es decir, datos en una relación primario\-secundario\) en controles WPF.  Para obtener más información, vea [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Tutorial: Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Información general](../Topic/WCF%20Data%20Services%20Overview.md)   
 [Información general de Entity Framework](../Topic/Entity%20Framework%20Overview.md)   
 [Información general sobre WPF y Silverlight Designer](http://msdn.microsoft.com/es-es/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Información general sobre el enlace de datos](../Topic/Data%20Binding%20Overview.md)