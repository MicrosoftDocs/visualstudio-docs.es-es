---
title: "Tutorial: Crear una aplicaci&#243;n de datos con n niveles | Microsoft Docs"
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
  - "aplicaciones con n capas, crear"
  - "aplicaciones con n capas, tutoriales"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear una aplicaci&#243;n de datos con n niveles
Las aplicaciones de datos con *n niveles* son aplicaciones que tienen acceso a datos y que están separadas en varias capas lógicas, o *niveles*.  Al separar los componentes de la aplicación en estos niveles individuales, se aumenta la facilidad de mantenimiento y la escalabilidad de la aplicación.  Esto se consigue mediante una integración más sencilla de nuevas tecnologías, que se pueden aplicar a un solo nivel sin necesidad de volver a diseñar la solución completa.  Una arquitectura típica con n niveles incluye un nivel de presentación, un nivel intermedio y una capa de datos.  El nivel intermedio incluye normalmente una capa de acceso a datos, una capa de la lógica empresarial y componentes compartidos, tales como autenticación y validación.  La capa de datos incluye una base de datos relacional.  Las aplicaciones con n niveles normalmente almacenan la información confidencial en la capa de acceso a datos del nivel intermedio para aislar esa información de los usuarios finales que obtienen acceso al nivel de presentación.  Para obtener más información, vea [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md).  
  
 Una manera de separar los distintos niveles de una aplicación con n niveles consiste en crear proyectos independientes para cada nivel que se desee incluir en la aplicación.  Los conjuntos de datos con tipo contienen una propiedad `DataSet Project` que determina en qué proyectos deben ir el conjunto de datos y el código de `TableAdapter` generados.  
  
 Este tutorial muestra cómo separar el código de conjunto de datos y `TableAdapter` en proyectos de bibliotecas de clases individuales mediante el **Diseñador de Dataset**.  Después de separar el código de conjunto de datos y TableAdapter, deberá crear un servicio [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) para realizar llamas al nivel de acceso a datos.  Finalmente, creará una aplicación de formularios Windows Forms como nivel de presentación.  Este nivel obtiene acceso a los datos desde el servicio de datos.  
  
 Durante este tutorial, llevará a cabo los siguientes pasos:  
  
-   Crear una nueva solución con n niveles que contendrá varios proyectos.  
  
-   Agregar dos proyectos de bibliotecas de clases a la solución con n niveles.  
  
-   Crear un conjunto de datos con tipo mediante el **Asistente para la configuración de orígenes de datos**.  
  
-   Separar en proyectos independientes el código de las clases de conjunto de datos y [TableAdapters](../Topic/TableAdapters.md) generado.  
  
-   Crear un servicio de Windows Communication Foundation \(WCF\) para realizar llamadas al nivel de acceso a datos.  
  
-   Crear funciones en el servicio para recuperar datos del nivel de acceso a datos.  
  
-   Crear una aplicación de formularios Windows Forms que actúe como nivel de presentación.  
  
-   Crear controles de formularios Windows Forms enlazados al origen de datos.  
  
-   Escribir código para rellenar las tablas de datos.  
  
 ![vínculo a vídeo](../data-tools/media/playvideo.png "PlayVideo") Para ver una versión en vídeo de este tema, vea el vídeo sobre [cómo crear una aplicación de datos con n niveles](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## Requisitos previos  
 Para completar este tutorial, necesita lo siguiente:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear la solución de n niveles y la biblioteca de clases que alberga el conjunto de datos \(DataEntityTier\)  
 El primer paso de este tutorial consiste en crear una solución y dos proyectos de biblioteca de clases.  La primera biblioteca de clases contendrá el conjunto de datos \(la clase de DataSet con tipo y las DataTables que contendrán los datos de la aplicación\).  Este proyecto se utiliza como la capa de entidad de datos de la aplicación, y se ubica normalmente en el nivel intermedio.  El [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) se utiliza para crear el conjunto de datos inicial y para separar automáticamente el código en las dos bibliotecas de clases.  
  
> [!NOTE]
>  Asegúrese de asignar el nombre correcto al proyecto y a la solución antes de hacer clic en **Aceptar**.  De este modo, será más fácil poder completar este tutorial.  
  
#### Para crear la solución con n niveles y la biblioteca de clases DataEntityTier  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
    > [!NOTE]
    >  El **Diseñador de DataSet** se puede utilizar en proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y C\#.  Cree el nuevo proyecto en uno de estos lenguajes.  
  
2.  En el panel **Tipos de proyecto** del cuadro de diálogo **Nuevo proyecto**, haga clic en **Windows**.  
  
3.  Haga clic en la plantilla **Biblioteca de clases**.  
  
4.  Asigne al proyecto el nombre DataEntityTier.  
  
5.  Asigne a la solución el nombre NTierWalkthrough.  
  
6.  Haga clic en **Aceptar**.  
  
     Se crea una solución NTierWalkthrough que contiene el proyecto DataEntityTier y se agrega al **Explorador de soluciones**.  
  
## Crear la biblioteca de clases para albergar los TableAdapters \(DataAccessTier\)  
 El paso siguiente después de crear el proyecto DataEntityTier consiste en crear otro proyecto de biblioteca de clases.  Este proyecto contendrá los `TableAdapter`s generados y constituye el *nivel de acceso a datos* de la aplicación.  El nivel de acceso a datos contiene la información que se requiere para conectarse a la base de datos, y se encuentra normalmente en el nivel intermedio.  
  
#### Para crear la nueva biblioteca de clases para los TableAdapters  
  
1.  En el menú **Archivo**, agregue un nuevo proyecto a la solución NTierWalkthrough.  
  
2.  En el panel **Plantillas** del cuadro de diálogo **Nuevo proyecto**, haga clic en **Biblioteca de clases**.  
  
3.  Denomine el proyecto DataAccessTier y haga clic en **Aceptar**.  
  
     Se crea el proyecto DataAccessTier y se agrega a la solución NTierWalkthrough.  
  
## Crear el conjunto de datos  
 El paso siguiente consiste en crear un conjunto de datos con tipo.  Los conjuntos de datos con tipo se crean con la clase de conjunto de datos \(incluidas las clases DataTables\) y las clases `TableAdapter` en un solo proyecto.  \(Todas las clases se generan en un solo archivo.\) Al separar el conjunto de datos y los `TableAdapter`s en proyectos diferentes, es la clase de conjunto de datos la que se traslada al otro proyecto, dejando las clases `TableAdapter` en el proyecto original.  Por consiguiente, cree el conjunto de datos en el proyecto que finalmente contendrá los `TableAdapter`s \(el proyecto DataAccessTier\).  Creará el conjunto de datos mediante el **Asistente para la configuración de orígenes de datos**.  
  
> [!NOTE]
>  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la forma de configurar la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear el conjunto de datos  
  
1.  Haga clic en DataAccessTier en el **Explorador de soluciones**.  
  
2.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
3.  En la ventana **Orígenes de datos**, haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
4.  En la página **Elegir un tipo de origen de datos**, haga clic en **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
5.  En la página **Elegir la conexión de datos**, realice una de las siguientes acciones:  
  
     Si existe alguna conexión de datos a la base de datos de ejemplo Northwind disponible en el cuadro de lista desplegable, haga clic en ella.  
  
     O bien  
  
     Haga clic en **Nueva conexión** para abrir el cuadro de diálogo **Agregar conexión**.  
  
6.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **Siguiente**.  
  
    > [!NOTE]
    >  Si ha seleccionado un archivo de base de datos local \(en lugar de conectarse a SQL Server\), se le podría preguntar si desea agregar el archivo al proyecto.  Haga clic en **Sí** para agregar el archivo de base de datos al proyecto.  
  
7.  Haga clic en **Siguiente** en la página **Guardar cadena de conexión en el archivo de configuración de la aplicación**.  
  
8.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.  
  
9. Haga clic en las casillas de las tablas **Customers** y **Orders** y, a continuación, haga clic en **Finalizar**.  
  
     NorthwindDataSet se agrega al proyecto DataAccessTier y aparece en la ventana **Orígenes de datos**.  
  
## Separar los TableAdapters del conjunto de datos  
 Después de crear el conjunto de datos, separe la clase de conjunto de datos generada de los TableAdapters.  Esto se hace configurando la propiedad **DataSet Project** con el nombre del proyecto en el que se va a almacenar la clase de conjunto de datos separada.  
  
#### Para separar los TableAdapters del conjunto de datos  
  
1.  Haga doble clic en **NorthwindDataSet.xsd** en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.  
  
2.  Haga clic en un área vacía del diseñador.  
  
3.  Busque el nodo **DataSet Project** en la ventana **Propiedades**.  
  
4.  En la lista **DataSet Project**, haga clic en **DataEntityTier**.  
  
5.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
 El conjunto de datos y los TableAdapters se separan en los dos proyectos de biblioteca de clases.  El proyecto que originalmente contenía el conjunto de datos entero \(DataAccessTier\) contiene ahora sólo los TableAdapters.  El proyecto designado en la propiedad **DataSet Project** \(DataEntityTier\) contiene el conjunto de datos con tipo: NorthwindDataSet.Dataset.Designer.vb \(o NorthwindDataSet.Dataset.Designer.cs\).  
  
> [!NOTE]
>  Cuando los conjuntos de datos se separan de los TableAdapters \(estableciendo la propiedad **DataSet Project**\), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente.  Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
## Crear una nueva aplicación de servicio  
 Dado que este tutorial muestra cómo obtener acceso al nivel de acceso a datos mediante un servicio WCF, deberá crear una nueva aplicación de servicio WCF.  
  
#### Para crear una nueva aplicación de servicio WCF  
  
1.  En el menú **Archivo**, agregue un nuevo proyecto a la solución NTierWalkthrough.  
  
2.  En el panel **Tipos de proyecto** del cuadro de diálogo **Nuevo proyecto**, haga clic en **WCF**.  En el panel **Plantillas**, haga clic en **Biblioteca de servicios de WCF**.  
  
3.  Denomine el proyecto DataService y haga clic en **Aceptar**.  
  
     Se crea el proyecto DataService y se agrega a la solución NTierWalkthrough.  
  
## Crear métodos en el nivel de acceso a datos para devolver los datos de clientes y pedidos  
 El servicio de datos tiene que llamar a dos métodos del nivel de acceso a datos: GetCustomers y GetOrders.  Estos métodos devolverán las tablas Customers y Orders de Northwind.  Cree los métodos GetCustomers y GetOrders en el proyecto DataAccessTier.  
  
#### Para crear un método en el nivel de acceso a datos que devuelva la tabla Customers  
  
1.  En el **Explorador de soluciones**, haga doble clic en el archivo NorthwindDataset.xsd para abrir el conjunto de datos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
2.  Haga clic con el botón secundario en CustomersTableAdapter y haga clic en **Agregar consulta** para abrir el [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md).  
  
3.  En la página **Elija un tipo de comando**, deje el valor predeterminado de **Usar instrucciones SQL** y haga clic en **Siguiente**.  
  
4.  En la página **Elija un tipo de consulta**, deje el valor predeterminado de **SELECT que devuelve filas** y haga clic en **Siguiente**.  
  
5.  En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.  
  
6.  En la página **Elija los métodos que se van a generar**, escriba GetCustomers como **Nombre del método** en la sección **Devolver un DataTable**.  
  
7.  Haga clic en **Finalizar**.  
  
#### Para crear un método en el nivel de acceso a datos que devuelva la tabla Orders  
  
1.  Haga clic con el botón secundario del mouse en OrdersTableAdapter y elija **Agregar consulta**.  
  
2.  En la página **Elija un tipo de comando**, deje el valor predeterminado de **Usar instrucciones SQL** y haga clic en **Siguiente**.  
  
3.  En la página **Elija un tipo de consulta**, deje el valor predeterminado de **SELECT que devuelve filas** y haga clic en **Siguiente**.  
  
4.  En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.  
  
5.  En la página **Elija los métodos que se van a generar**, escriba GetOrders como **Nombre del método** en la sección **Devolver un DataTable**.  
  
6.  Haga clic en **Finalizar**.  
  
7.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
## Agregar una referencia a los niveles de entidad de datos y acceso a datos en el servicio de datos  
 Dado que el servicio de datos requiere información del conjunto de datos y los TableAdapters, agregue referencias a los proyectos DataEntityTier y DataAccessTier.  
  
#### Para agregar referencias al servicio de datos  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en DataService y, a continuación, haga clic en **Agregar referencia**.  
  
2.  En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos**.  
  
3.  Seleccione los proyectos **DataAccessTier** y **DataEntityTier**.  
  
4.  Haga clic en **Aceptar**.  
  
## Agregar funciones al servicio para llamar a los métodos GetCustomers y GetOrders del nivel de acceso a datos  
 Ahora que el nivel de acceso a datos contiene los métodos para devolver los datos, cree los métodos correspondientes en el servicio de datos para llamar a esos métodos del nivel de acceso a datos.  
  
> [!NOTE]
>  Para los proyectos de C\#, deberá agregar una referencia al ensamblado `System.Data.DataSetExtensions` a fin de que el código siguiente pueda compilarse.  
  
#### Para crear las funciones GetCustomers y GetOrders en el servicio de datos  
  
1.  En el proyecto **DataService**, haga doble clic en IService1.vb o IService1.cs.  
  
2.  Agregue el código siguiente debajo del comentario **Agregue aquí las operaciones del servicio**:  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  En el proyecto DataService, haga doble clic en Service1.vb \(or Service1.cs\).  
  
4.  Agregue el código siguiente a la clase Service1.  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
  
    }  
    ```  
  
5.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
## Crear un nivel de presentación para mostrar los datos del servicio de datos  
 Ahora que la solución contiene el servicio de datos con métodos que realizan llamadas al nivel de acceso a datos, cree otro proyecto que realizará llamadas al servicio de datos y presentará los datos a los usuarios.  Para este tutorial, cree una aplicación de formularios Windows Forms; éste es el nivel de presentación de la aplicación con n niveles.  
  
#### Para crear el proyecto de nivel de presentación  
  
1.  En el menú **Archivo**, agregue un nuevo proyecto a la solución NTierWalkthrough.  
  
2.  En el panel **Tipos de proyecto** del cuadro de diálogo **Nuevo proyecto**, haga clic en **Windows**.  En el panel **Plantillas**, haga clic en **Aplicación de Windows Forms**.  
  
3.  Denomine el proyecto PresentationTier y haga clic en **Aceptar**.  
  
4.  Se crea el proyecto PresentationTier y se agrega a la solución NTierWalkthrough.  
  
## Establecer el proyecto PresentationTier como proyecto de inicio  
 Dado que el nivel de presentación es la aplicación cliente real que se utiliza para presentar e interactuar con los datos, deberá establecer el proyecto PresentationTier como proyecto de inicio.  
  
#### Para establecer el nuevo proyecto de nivel de presentación como proyecto de inicio  
  
-   En el **Explorador de soluciones**, haga clic con el botón secundario en **PresentationTier** y, a continuación, haga clic en **Establecer como proyecto de inicio**.  
  
## Agregar referencias al nivel de presentación  
 La aplicación cliente PresentationTier requiere una referencia de servicio al servicio de datos para poder tener acceso a los métodos del servicio.  Además, se requiere una referencia al conjunto de datos para que el servicio WCF pueda compartir los tipos.  Mientras no se habilite el uso compartido de tipos a través del servicio de datos, el código agregado a la clase de conjunto de datos parcial no estará disponible en el nivel de presentación.  Como normalmente se agrega código, tal como el código de validación para los eventos de cambio de fila y columna de una tabla de datos, es probable que desee tener acceso a este código desde el cliente.  
  
#### Para agregar una referencia al nivel de presentación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en PresentationTier y, a continuación, haga clic en **Agregar referencia**.  
  
2.  En el cuadro de diálogo **Agregar referencia**, seleccione la ficha **Proyectos**.  
  
3.  Seleccione **DataEntityTier** y haga clic en **Aceptar**.  
  
#### Para agregar una referencia de servicio al nivel de presentación  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en PresentationTier y, a continuación, haga clic en **Agregar referencia de servicio**.  
  
2.  En el cuadro de diálogo **Agregar referencia de servicio**, haga clic en **Detectar**.  
  
3.  Seleccione **Service1** y haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si dispone de varios servicios en el equipo actual, seleccione el servicio que creó previamente en este tutorial \(el servicio que contiene los métodos GetCustomers y GetOrders\).  
  
## Agregar DataGridViews al formulario para mostrar los datos devueltos por el servicio de datos  
 Después de agregar la referencia de servicio al servicio de datos, la ventana **Orígenes de datos** se rellena automáticamente con los datos devueltos por el servicio.  
  
#### Para agregar al formulario Windows Forms dos DataGridViews enlazados a datos  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto PresentationTier.  
  
2.  En la ventana **Orígenes de datos**, expanda **NorthwindDataSet** y busque el nodo **Customers**.  
  
3.  Arrastre el nodo **Customers** hasta Form1.  
  
4.  En la ventana **Orígenes de datos**, expanda el nodo **Customers** y busque el nodo **Orders** relacionado \(el nodo **Orders** anidado dentro del nodo **Customers**\).  
  
5.  Arrastre el nodo **Orders** relacionado hasta Form1.  
  
6.  Cree un controlador de eventos para el evento `Form1_Load` haciendo doble clic sobre un área vacía del formulario.  
  
7.  Agregue el código siguiente al controlador de eventos `Form1_Load`.  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## Aumentar el tamaño máximo de mensaje permitido por el servicio  
 Puesto que el servicio devuelve datos de las tablas Customers y Orders, el valor predeterminado de maxReceivedMessageSize no es suficientemente grande para contener los datos, por lo que dicho valor se debe aumentar.  Para este tutorial, cambiará el valor por 6553600.  Cambiará este valor en el cliente y esto actualizará automáticamente la referencia de servicio.  
  
> [!NOTE]
>  El tamaño predeterminado más bajo está pensado para limitar la exposición a ataques por denegación de servicio \(DOS\).  Para obtener más información, vea <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### Para aumentar el valor de maxReceivedMessageSize  
  
1.  En el **Explorador de soluciones**, haga doble clic en el archivo app.config del proyecto PresentationTier.  
  
2.  Busque el atributo de tamaño **maxReceivedMessage** y cambie su valor a `6553600`.  
  
## Probar la aplicación  
 Ejecute la aplicación.  Los datos se recuperan del servicio de datos y se muestran en el formulario.  
  
#### Para probar la aplicación  
  
1.  Presione F5.  
  
2.  Los datos de las tablas Customers y Orders se recuperan del servicio de datos y se muestran en el formulario.  
  
## Pasos siguientes  
 En función de los requisitos de la aplicación, hay varios pasos que es posible que desee realizar después de guardar los datos relacionados en la aplicación basada en Windows.  Por ejemplo, a continuación se indican algunas de las mejoras que podría realizar en esta aplicación:  
  
-   Agregar validación al conjunto de datos.  Para obtener más información, vea [Tutorial: Agregar validación a una aplicación de datos con n niveles](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md).  
  
-   Agregar métodos adicionales al servicio para actualizar los datos de nuevo en la base de datos.  
  
## Vea también  
 [Trabajar con conjuntos de datos en aplicaciones de n capas](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)