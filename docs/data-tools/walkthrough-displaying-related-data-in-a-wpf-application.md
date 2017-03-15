---
title: "Tutorial: Mostrar datos relacionados en una aplicaci&#243;n WPF | Microsoft Docs"
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
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Mostrar datos relacionados en una aplicaci&#243;n WPF
En este tutorial, creará una aplicación WPF que muestre los datos de las tablas de base de datos que tengan una relación primaria\-secundaria.  Los datos se encapsulan en entidades en un Entity Data Model.  La entidad primaria contiene información general para un conjunto de pedidos.  Cada propiedad de esta entidad se enlaza a un control diferente de la aplicación.  La entidad secundaria contiene los detalles de cada pedido.  Este conjunto de datos se enlaza a un control <xref:System.Windows.Controls.DataGrid>.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear una aplicación WPF y un Entity Data Model generado con datos de la base de datos de ejemplo AdventureWorksLT.  
  
-   Crear un conjunto de controles enlazados a datos que muestran información general para un conjunto de pedidos.  Para crear los controles, se arrastra una entidad primaria desde la ventana **Orígenes de datos** hasta **WPF Designer**.  
  
-   Crear un control <xref:System.Windows.Controls.DataGrid> que muestre los detalles relacionados de cada pedido seleccionado.  Para crear los controles, se arrastra una entidad secundaria desde la ventana **Orígenes de datos** hasta una ventana de **WPF Designer**.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Acceso a una instancia en ejecución de SQL Server o SQL Server Express que tenga adjunta la base de datos de ejemplo AdventureWorksLT.  La base de datos AdventureWorksLT se puede descargar desde el [sitio web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Para completar el tutorial, resulta útil, aunque no necesario, tener conocimiento previo de los siguientes conceptos:  
  
-   Entity Data Model y ADO.NET Entity Framework.  Para obtener más información, vea [Información general de Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Uso de WPF Designer.  Para obtener más información, vea [Información general sobre WPF y Silverlight Designer](http://msdn.microsoft.com/es-es/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Enlace de datos de WPF.  Para obtener más información, vea [Información general sobre el enlace de datos](../Topic/Data%20Binding%20Overview.md).  
  
## Crear el proyecto  
 Cree un nuevo proyecto de WPF para mostrar los registros de pedidos.  
  
#### Para crear un proyecto nuevo de WPF  
  
1.  Inicie Visual Studio.  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  Expanda **Visual C\#** o **Visual Basic** y, a continuación, seleccione **Windows**.  
  
4.  Asegúrese de que **.NET Framework 4** esté seleccionado en el cuadro combinado de la parte superior del cuadro de diálogo.  El control <xref:System.Windows.Controls.DataGrid> que se usa en este tutorial solamente está disponible en .NET Framework 4.  
  
5.  Seleccione la plantilla de proyecto **Aplicación WPF**.  
  
6.  En el cuadro **Nombre**, escriba `AdventureWorksOrdersViewer`.  
  
7.  Haga clic en **Aceptar**.  
  
     Visual Studio crea el proyecto `AdventureWorksOrdersViewer`.  
  
## Crear un Entity Data Model para la aplicación  
 Para poder crear controles enlazados a datos, se debe definir un modelo de datos para la aplicación y se debe agregar a la ventana **Orígenes de datos**.  En este tutorial, el modelo de datos es un Entity Data Model.  
  
#### Para crear un Entity Data Model  
  
1.  En el menú **Datos**, haga clic en **Agregar nuevo origen de datos** para abrir el **Asistente para la configuración de orígenes de datos**.  
  
2.  En la página **Elegir un tipo de origen de datos**, haga clic en **Base de datos** y luego en **Siguiente**.  
  
3.  En la página **Elegir un modelo de base de datos**, haga clic en **Entity Data Model** y, a continuación, haga clic en **Siguiente**.  
  
4.  En la página **Elegir contenido de Model**, haga clic en **Generar desde la base de datos** y, a continuación, haga clic en **Siguiente**.  
  
5.  En la página **Elegir la conexión de datos**, realice una de las acciones siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo AdventureWorksLT está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Haga clic en **Nueva conexión** y cree una conexión a la base de datos AdventureWorksLT.  
  
     Asegúrese de que esté seleccionada la opción **Guardar configuración de conexión de la entidad en App.Config como** y, a continuación, haga clic en **Siguiente**.  
  
6.  En la página **Elija los objetos de base de datos**, expanda **Tablas** y, a continuación, seleccione las tablas siguientes.  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Haga clic en **Finalizar**.  
  
8.  Compile el proyecto.  
  
## Crear controles enlazados a datos que muestren los pedidos  
 Para crear controles que muestren los registros de pedidos, arrastre la entidad `SalesOrderHeaders` desde la ventana **Orígenes de datos** hasta WPF Designer.  
  
#### Para crear controles enlazados a datos que muestren los registros de pedidos  
  
1.  En el **Explorador de soluciones** haga doble clic en MainWindow.xaml.  
  
     La ventana se abrirá en WPF Designer.  
  
2.  Edite el XAML de modo que las propiedades **Height** y **Width** estén establecidas en 800.  
  
3.  En la ventana **Orígenes de datos**, haga clic en el menú desplegable del nodo **SalesOrderHeaders** y seleccione **Detalles**.  
  
4.  Expanda el nodo **SalesOrderHeaders**.  
  
5.  Haga clic en el menú desplegable al lado de **SalesOrderID** y seleccione **ComboBox**.  
  
6.  Haga clic en el menú desplegable situado al lado de cada uno de los siguientes nodos secundarios del nodo **SalesOrderHeaders** y seleccione **Ninguno**:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Carga**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Esta acción evita que Visual Studio cree controles enlazados a datos para estos nodos en el paso siguiente.  En este tutorial se supone que el usuario final no necesita ver estos datos.  
  
7.  En la ventana **Orígenes de datos**, arrastre el nodo **SalesOrderHeaders** hasta la ventana de **WPF Designer**.  
  
     Visual Studio genera XAML que crea un conjunto de controles que se enlazan a los datos de la entidad **SalesOrderHeaders**, además del código que carga los datos.  Para obtener más información sobre el XAML y el código generados, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  En el diseñador, haga clic en el cuadro combinado que está al lado de la etiqueta **Sales Order ID**.  
  
9. En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.  
  
## Crear un control DataGrid que muestre los detalles del pedido  
 Cree un control <xref:System.Windows.Controls.DataGrid> que muestre los detalles del pedido. Para ello, arrastre la entidad `SalesOrderDetails` desde la ventana **Orígenes de datos** hasta WPF Designer.  
  
#### Para crear un control DataGrid que muestre los detalles del pedido  
  
1.  En la ventana **Orígenes de datos**, busque el nodo **SalesOrderDetails** que es un elemento secundario del nodo **SalesOrderHeaders**.  
  
    > [!NOTE]
    >  Hay también un nodo **SalesOrderDetails** que es un elemento del mismo nivel del nodo **SalesOrderHeaders**.  Asegúrese de que selecciona el nodo secundario del nodo **SalesOrderHeaders**.  
  
2.  Expanda el nodo secundario **SalesOrderDetails**.  
  
3.  Haga clic en el menú desplegable situado al lado de cada uno de los siguientes nodos secundarios del nodo **SalesOrderDetails** y seleccione **Ninguno**:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Esta acción evita que Visual Studio incluya estos datos en el control <xref:System.Windows.Controls.DataGrid> que va a crear en el paso siguiente.  En este tutorial se supone que el usuario final no necesita ver estos datos.  
  
4.  Arrastre el nodo secundario **SalesOrderDetails** desde la ventana **Orígenes de datos** hasta la ventana de **WPF Designer**.  
  
     Visual Studio genera XAML para definir un nuevo control <xref:System.Windows.Controls.DataGrid> enlazado a datos y el control aparece en el diseñador.  Visual Studio también actualiza el método `GetSalesOrderHeadersQuery` generado en el archivo de código subyacente para incluir los datos en la entidad **SalesOrderDetails**.  
  
## Probar la aplicación  
 Compile y ejecute la aplicación para comprobar que muestra los registros de pedidos.  
  
#### Para probar la aplicación  
  
1.  Presione **F5**.  
  
     La aplicación se compila y se ejecuta.  Compruebe lo siguiente:  
  
    -   En el cuadro combinado **Sales Order ID**, se debe mostrar **71774**.  Es el primer identificador de pedido de la entidad.  
  
    -   Se mostrarán los detalles de cada pedido que seleccione en el cuadro combinado **Sales Order ID** de <xref:System.Windows.Controls.DataGrid>.  
  
2.  Cierre la aplicación.  
  
## Pasos siguientes  
 Después de completar este tutorial, puede aprender a usar la ventana **Orígenes de datos** de Visual Studio para enlazar controles WPF a otros tipos de orígenes de datos.  Para obtener más información, vea [Tutorial: Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) y [Tutorial: Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Cómo: Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)