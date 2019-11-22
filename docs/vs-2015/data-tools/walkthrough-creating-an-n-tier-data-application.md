---
title: 'Walkthrough: Creating an N-Tier Data Application | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bd77006eda03b716e3c54c0b5b52ac633a383377
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299596"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Tutorial: Crear una aplicación de datos con n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-tier* data applications are applications that access data and are separated into multiple logical layers, or *tiers*. Al separar los componentes de la aplicación en estos niveles individuales, se aumenta la facilidad de mantenimiento y la escalabilidad de la aplicación. Esto se consigue mediante una integración más sencilla de nuevas tecnologías, que se pueden aplicar a un solo nivel sin necesidad de volver a diseñar la solución completa. Una arquitectura típica con n niveles incluye un nivel de presentación, un nivel intermedio y una capa de datos. El nivel intermedio incluye normalmente una capa de acceso a datos, una capa de la lógica empresarial y componentes compartidos, tales como autenticación y validación. La capa de datos incluye una base de datos relacional. Las aplicaciones con n niveles normalmente almacenan la información confidencial en la capa de acceso a datos del nivel intermedio para aislar esa información de los usuarios finales que obtienen acceso al nivel de presentación. For more information, see [N-Tier Data Applications Overview](../data-tools/n-tier-data-applications-overview.md).

 Una manera de separar los distintos niveles de una aplicación con n niveles consiste en crear proyectos independientes para cada nivel que se desee incluir en la aplicación. Los conjuntos de datos con tipo contienen una propiedad `DataSet Project` que determina en qué proyectos deben ir el conjunto de datos y el código de `TableAdapter` generados.

 Este tutorial muestra cómo separar el código de conjunto de datos y `TableAdapter` en proyectos de bibliotecas de clases individuales mediante el **Diseñador de DataSet**. After you separate the dataset and TableAdapter code, you will create a [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) service to call into the data access tier. Finalmente, creará una aplicación de Windows Forms como nivel de presentación. Este nivel obtiene acceso a los datos desde el servicio de datos.

 Durante este tutorial, llevará a cabo los siguientes pasos:

- Crear una nueva solución con n niveles que contendrá varios proyectos.

- Agregar dos proyectos de bibliotecas de clases a la solución con n niveles.

- Cree un conjunto de datos con tipo mediante el **Asistente para configuración de orígenes de datos**.

- Separate the generated [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) and dataset code into discrete projects.

- Crear un servicio de Windows Communication Foundation (WCF) para realizar llamadas al nivel de acceso a datos.

- Crear funciones en el servicio para recuperar datos del nivel de acceso a datos.

- Crear una aplicación de Windows Forms que actúe como nivel de presentación.

- Crear controles de formularios Windows Forms enlazados al origen de datos.

- Escribir código para rellenar las tablas de datos.

  ![link to video](../data-tools/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Creating an N-Tier Data Application](https://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Requisitos previos
 Para completar este tutorial, necesita lo siguiente:

- Acceso a la base de datos de ejemplo Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Crear la solución de n niveles y la biblioteca de clases que alberga el conjunto de datos (DataEntityTier)
 El primer paso de este tutorial consiste en crear una solución y dos proyectos de biblioteca de clases. La primera biblioteca de clases contendrá el conjunto de datos (la clase de DataSet con tipo y las DataTables que contendrán los datos de la aplicación). Este proyecto se utiliza como la capa de entidad de datos de la aplicación, y se ubica normalmente en el nivel intermedio. The Dataset Designer is used to create the initial dataset and automatically separate the code into the two class libraries.

> [!NOTE]
> Asegúrese de asignar el nombre correcto al proyecto y a la solución antes de hacer clic en **Aceptar**. De este modo, será más fácil poder completar este tutorial.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Para crear la solución con n niveles y la biblioteca de clases DataEntityTier

1. From the **File** menu, create a new project.

    > [!NOTE]
    > The **Dataset Designer** is supported in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and C# projects. Cree el nuevo proyecto en uno de estos lenguajes.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**.

3. Click the **Class Library** template.

4. Asigne al proyecto el nombre **DataEntityTier**.

5. Name the solution **NTierWalkthrough**.

6. Haga clic en **Aceptar**.

     Se crea una solución NTierWalkthrough que contiene el proyecto DataEntityTier y se agrega al **Explorador de soluciones**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Crear la biblioteca de clases para albergar los TableAdapters (DataAccessTier)
 El paso siguiente después de crear el proyecto DataEntityTier consiste en crear otro proyecto de biblioteca de clases. This project will hold the generated `TableAdapter`s and is called the *data access tier* of the application. El nivel de acceso a datos contiene la información que se requiere para conectarse a la base de datos, y se encuentra normalmente en el nivel intermedio.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Para crear la nueva biblioteca de clases para los TableAdapters

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Templates** pane, click **Class Library**.

3. Name the project **DataAccessTier** and click **OK**.

     Se crea el proyecto DataAccessTier y se agrega a la solución NTierWalkthrough.

## <a name="creating-the-dataset"></a>Crear el conjunto de datos
 El paso siguiente consiste en crear un conjunto de datos con tipo. Los conjuntos de datos con tipo se crean con la clase de conjunto de datos (incluidas las clases DataTables) y las clases `TableAdapter` en un solo proyecto. (All classes are generated into a single file.) When you separate the dataset and `TableAdapter`s into different projects, it is the dataset class that is moved to the other project, leaving the `TableAdapter` classes in the original project. Por consiguiente, cree el conjunto de datos en el proyecto que finalmente contendrá los `TableAdapter`s (el proyecto DataAccessTier). You will create the dataset by using the **Data Source Configuration Wizard**.

> [!NOTE]
> Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.

#### <a name="to-create-the-dataset"></a>Para crear el conjunto de datos

1. Click DataAccessTier in **Solution Explorer**.

2. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

3. In the **Data Sources** window, click **Add New Data Source** to start the **Data Source Configuration Wizard**.

4. On the **Choose a Data Source Type** page, click **Database** and then click **Next**.

5. En la página **Elegir la conexión de datos**, realice una de las siguientes acciones:

     Si existe alguna conexión de datos a la base de datos de ejemplo Northwind disponible en el cuadro de lista desplegable, haga clic en ella.

     o bien

     Click **New Connection** to open the **Add Connection** dialog box.

6. Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **Siguiente**.

    > [!NOTE]
    > Si ha seleccionado un archivo de base de datos local (en lugar de conectarse a SQL Server), se le podría preguntar si desea agregar el archivo al proyecto. Click **Yes** to add the database file to the project.

7. Click **Next** on the **Save the Connection String to the Application Configuration File** page.

8. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos** .

9. Click the check boxes for the **Customers** and **Orders** tables, and then click **Finish**.

     NorthwindDataSet se agrega al proyecto DataAccessTier y aparece en la ventana **Orígenes de datos**.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Separar los TableAdapters del conjunto de datos
 Después de crear el conjunto de datos, separe la clase de conjunto de datos generada de los TableAdapters. Esto se hace configurando la propiedad **DataSet Project** con el nombre del proyecto en el que se va a almacenar la clase de conjunto de datos separada.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Para separar los TableAdapters del conjunto de datos

1. Haga doble clic en **NorthwindDataSet.xsd** en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.

2. Haga clic en un área vacía del diseñador.

3. Busque el nodo **DataSet Project** en la ventana **Propiedades**.

4. In the **DataSet Project** list, click **DataEntityTier**.

5. En el menú **Compilar** , haga clic en **Compilar solución**.

   El conjunto de datos y los TableAdapters se separan en los dos proyectos de biblioteca de clases. El proyecto que originalmente contenía el conjunto de datos entero (DataAccessTier) contiene ahora sólo los TableAdapters. The project designated in the **DataSet Project** property (DataEntityTier) contains the typed dataset: NorthwindDataSet.Dataset.Designer.vb (or NorthwindDataSet.Dataset.Designer.cs).

> [!NOTE]
> Cuando los conjuntos de datos se separan de los TableAdapters (estableciendo la propiedad **DataSet Project**), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

## <a name="creating-a-new-service-application"></a>Crear una nueva aplicación de servicio
 Dado que este tutorial muestra cómo obtener acceso al nivel de acceso a datos mediante un servicio WCF, deberá crear una nueva aplicación de servicio WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Para crear una nueva aplicación de servicio WCF

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **WCF**. In the **Templates** pane, click **WCF Service Library**.

3. Name the project **DataService** and click **OK**.

     Se crea el proyecto DataService y se agrega a la solución NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Crear métodos en el nivel de acceso a datos para devolver los datos de clientes y pedidos
 El servicio de datos tiene que llamar a dos métodos del nivel de acceso a datos: GetCustomers y GetOrders. Estos métodos devolverán las tablas Customers y Orders de Northwind. Cree los métodos GetCustomers y GetOrders en el proyecto DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Customers

1. In **Solution Explorer**, double-click NorthwindDataset.xsd to open the dataset in the Dataset Designer.

2. Right-click CustomersTableAdapter and click **Add Query** to edit the Tableadapter.

3. En la página **Elija un tipo de comando**, deje el valor predeterminado **Usar instrucciones SQL** y haga clic en **Siguiente**.

4. En la página **Elija un tipo de consulta**, deje el valor predeterminado **SELECT que devuelve filas** y haga clic en **Siguiente**.

5. En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.

6. En la página **Elija los métodos que se van a generar**, escriba **GetCustomers** como **Nombre del método** en la sección **Devolver un DataTable**.

7. Haga clic en **Finalizar**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Orders

1. Right-click OrdersTableAdapter and click **Add Query**.

2. En la página **Elija un tipo de comando**, deje el valor predeterminado **Usar instrucciones SQL** y haga clic en **Siguiente**.

3. En la página **Elija un tipo de consulta**, deje el valor predeterminado **SELECT que devuelve filas** y haga clic en **Siguiente**.

4. En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.

5. En la página **Elija los métodos que se van a generar**, escriba **GetOrders** como **Nombre del método** en la sección **Devolver un DataTable**.

6. Haga clic en **Finalizar**.

7. En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Agregar una referencia a los niveles de entidad de datos y acceso a datos en el servicio de datos
 Dado que el servicio de datos requiere información del conjunto de datos y los TableAdapters, agregue referencias a los proyectos DataEntityTier y DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Para agregar referencias al servicio de datos

1. Right-click DataService in **Solution Explorer** and click **Add Reference**.

2. En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos**.

3. Seleccione los proyectos **DataAccessTier** y **DataEntityTier**.

4. Haga clic en **Aceptar**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Agregar funciones al servicio para llamar a los métodos GetCustomers y GetOrders del nivel de acceso a datos
 Ahora que el nivel de acceso a datos contiene los métodos para devolver los datos, cree los métodos correspondientes en el servicio de datos para llamar a esos métodos del nivel de acceso a datos.

> [!NOTE]
> Para los proyectos de C#, deberá agregar una referencia al ensamblado `System.Data.DataSetExtensions` a fin de que el código siguiente pueda compilarse.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Para crear las funciones GetCustomers y GetOrders en el servicio de datos

1. In the **DataService** project, double-click IService1.vb or IService1.cs.

2. Agregue el código siguiente debajo del comentario **Agregue aquí las operaciones del servicio**:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();

    ```

3. En el proyecto DataService, haga doble clic en Service1.vb (or Service1.cs).

4. Agregue el código siguiente a la clase Service1.

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
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

5. En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Crear un nivel de presentación para mostrar los datos del servicio de datos
 Ahora que la solución contiene el servicio de datos con métodos que realizan llamadas al nivel de acceso a datos, cree otro proyecto que realizará llamadas al servicio de datos y presentará los datos a los usuarios. Para este tutorial, cree una aplicación de formularios Windows Forms; éste es el nivel de presentación de la aplicación con n niveles.

#### <a name="to-create-the-presentation-tier-project"></a>Para crear el proyecto de nivel de presentación

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**. En el panel **Plantillas** , haga clic en **Aplicación de Windows Forms**.

3. Denomine el proyecto **PresentationTier** y haga clic en **Aceptar**.

4. Se crea el proyecto PresentationTier y se agrega a la solución NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Establecer el proyecto PresentationTier como proyecto de inicio
 Dado que el nivel de presentación es la aplicación cliente real que se utiliza para presentar e interactuar con los datos, deberá establecer el proyecto PresentationTier como proyecto de inicio.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Para establecer el nuevo proyecto de nivel de presentación como proyecto de inicio

- En el **Explorador de soluciones**, haga clic con el botón derecho en **PresentationTier** y después haga clic en **Establecer como proyecto de inicio**.

## <a name="adding-references-to-the-presentation-tier"></a>Agregar referencias al nivel de presentación
 La aplicación cliente PresentationTier requiere una referencia de servicio al servicio de datos para poder tener acceso a los métodos del servicio. Además, se requiere una referencia al conjunto de datos para que el servicio WCF pueda compartir los tipos. Mientras no se habilite el uso compartido de tipos a través del servicio de datos, el código agregado a la clase de conjunto de datos parcial no estará disponible en el nivel de presentación. Como normalmente se agrega código, tal como el código de validación para los eventos de cambio de fila y columna de una tabla de datos, es probable que desee tener acceso a este código desde el cliente.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Para agregar una referencia al nivel de presentación

1. In **Solution Explorer**, right-click PresentationTier and click **Add Reference**.

2. In the **Add Reference** dialog box, click the **Projects** tab.

3. Select **DataEntityTier** and click **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Para agregar una referencia de servicio al nivel de presentación

1. In **Solution Explorer**, right-click PresentationTier and click **Add Service Reference**.

2. En el cuadro de diálogo **Agregar referencia de servicio**, haga clic en **Detectar**.

3. Select **Service1** and click **OK**.

    > [!NOTE]
    > Si dispone de varios servicios en el equipo actual, seleccione el servicio que creó previamente en este tutorial (el servicio que contiene los métodos GetCustomers y GetOrders).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Agregar DataGridViews al formulario para mostrar los datos devueltos por el servicio de datos
 Después de agregar la referencia de servicio al servicio de datos, la ventana **Orígenes de datos** se rellena automáticamente con los datos devueltos por el servicio.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Para agregar al formulario Windows Forms dos DataGridViews enlazados a datos

1. In **Solution Explorer**, select the PresentationTier project.

2. En la ventana **Orígenes de datos**, expanda **NorthwindDataSet** y busque el nodo **Customers**.

3. Arrastre el nodo **Customers** hasta Form1.

4. En la ventana **Orígenes de datos**, expanda el nodo **Customers** y busque el nodo **Orders** relacionado (el nodo **Orders** anidado dentro del nodo **Customers**).

5. Arrastre el nodo **Orders** relacionado hasta Form1.

6. Cree un controlador de eventos para el evento `Form1_Load` haciendo doble clic sobre un área vacía del formulario.

7. Agregue el código siguiente al controlador de eventos `Form1_Load`.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());

    ```

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Aumentar el tamaño máximo de mensaje permitido por el servicio
 Puesto que el servicio devuelve datos de las tablas Customers y Orders, el valor predeterminado de maxReceivedMessageSize no es suficientemente grande para contener los datos, por lo que dicho valor se debe aumentar. Para este tutorial, cambiará el valor por 6553600. Cambiará este valor en el cliente y esto actualizará automáticamente la referencia de servicio.

> [!NOTE]
> El tamaño predeterminado más bajo está pensado para limitar la exposición a ataques por denegación de servicio (DOS). Para obtener más información, vea <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Para aumentar el valor de maxReceivedMessageSize

1. In **Solution Explorer**, double-click the app.config file in the PresentationTier project.

2. Busque el atributo de tamaño **maxReceivedMessage** y cambie su valor a `6553600`.

## <a name="testing-the-application"></a>Probar la aplicación
 Ejecute la aplicación. Los datos se recuperan del servicio de datos y se muestran en el formulario.

#### <a name="to-test-the-application"></a>Para probar la aplicación

1. Presione F5.

2. Los datos de las tablas Customers y Orders se recuperan del servicio de datos y se muestran en el formulario.

## <a name="next-steps"></a>Pasos siguientes
 En función de los requisitos de la aplicación, hay varios pasos que es posible que desee realizar después de guardar los datos relacionados en la aplicación basada en Windows. Por ejemplo, a continuación se indican algunas de las mejoras que podría realizar en esta aplicación:

- Agregar validación al conjunto de datos. For information, see [Walkthrough: Adding Validation to an N-Tier Data Application](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Agregar métodos adicionales al servicio para actualizar los datos de nuevo en la base de datos.

## <a name="see-also"></a>Vea también
 [Work with datasets in n-tier applications](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hierarchical update](../data-tools/hierarchical-update.md) [Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
