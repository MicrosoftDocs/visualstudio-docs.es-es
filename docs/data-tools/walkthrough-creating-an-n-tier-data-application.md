---
title: 'Tutorial: Crear una aplicación de datos con n niveles'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 87b88c6fc8c6add2c93721b46165ffd295f4d614
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942899"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Tutorial: Crear una aplicación de datos con n niveles
*N niveles* aplicaciones de datos son las aplicaciones que acceden a datos y se dividen en varias capas lógicas, o *niveles*. Al separar los componentes de la aplicación en estos niveles individuales, se aumenta la facilidad de mantenimiento y la escalabilidad de la aplicación. Esto se consigue mediante una integración más sencilla de nuevas tecnologías, que se pueden aplicar a un solo nivel sin necesidad de volver a diseñar la solución completa. Una arquitectura típica con n niveles incluye un nivel de presentación, un nivel intermedio y una capa de datos. El nivel intermedio incluye normalmente una capa de acceso a datos, una capa de la lógica empresarial y componentes compartidos, tales como autenticación y validación. La capa de datos incluye una base de datos relacional. Las aplicaciones con n niveles normalmente almacenan la información confidencial en la capa de acceso a datos del nivel intermedio para aislar esa información de los usuarios finales que obtienen acceso al nivel de presentación. Para obtener más información, consulte [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).

Una manera de separar los distintos niveles de una aplicación con n niveles consiste en crear proyectos independientes para cada nivel que se desee incluir en la aplicación. Los conjuntos de datos con tipo contienen una propiedad `DataSet Project` que determina en qué proyectos deben ir el conjunto de datos y el código de `TableAdapter` generados.

En este tutorial muestra cómo separar el conjunto de datos y `TableAdapter` código en proyectos de biblioteca de clases individuales mediante el uso de la **Diseñador de Dataset**. Después de separar el conjunto de datos y el código de TableAdapter, se crea un [servicios Windows Communication Foundation y WCF Data Services en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) servicio para llamar a la capa de acceso a datos. Por último, cree una aplicación de Windows Forms como nivel de presentación. Este nivel obtiene acceso a los datos desde el servicio de datos.

Durante este tutorial, realice los pasos siguientes:

-   Cree una nueva solución de n niveles que contiene varios proyectos.

-   Agregar dos proyectos de bibliotecas de clases a la solución con n niveles.

-   Crear un conjunto de datos con tipo mediante el **Asistente para configuración de origen de datos**.

-   Separar generado [TableAdapters](create-and-configure-tableadapters.md) y el código del conjunto de datos en proyectos discretos.

-   Crear un servicio de Windows Communication Foundation (WCF) para realizar llamadas al nivel de acceso a datos.

-   Crear funciones en el servicio para recuperar datos del nivel de acceso a datos.

-   Crear una aplicación de formularios Windows Forms que actúe como nivel de presentación.

-   Crear controles de formularios Windows Forms enlazados al origen de datos.

-   Escribir código para rellenar las tablas de datos.

![vínculo a vídeo](../data-tools/media/playvideo.gif) para una versión en vídeo de este tema, consulte [vídeo sobre cómo: crear una aplicación de datos con n niveles](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Requisitos previos
En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **desarrollo de escritorio de .NET** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (**Explorador de objetos de SQL Server** se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Crear la biblioteca de clase y de solución con n niveles para contener el conjunto de datos (DataEntityTier)
 El primer paso de este tutorial consiste en crear una solución y dos proyectos de biblioteca de clases. La biblioteca de primera clase contiene el conjunto de datos (con tipo generado `DataSet` clase y las DataTables que contienen datos de la aplicación). Este proyecto se utiliza como la capa de entidad de datos de la aplicación, y se ubica normalmente en el nivel intermedio. El conjunto de datos crea el conjunto de datos inicial y separa automáticamente el código en las bibliotecas de dos clases.

> [!NOTE]
> No olvide el nombre del proyecto y solución correctamente antes de hacer clic **Aceptar**. De este modo, será más fácil poder completar este tutorial.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Para crear la solución con n niveles y la biblioteca de clases DataEntityTier 

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **biblioteca de clases** tipo de proyecto.

4. Denomine el proyecto **DataEntityTier**.

5. Nombre de la solución **NTierWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea y se agrega a una solución NTierWalkthrough que contiene el proyecto DataEntityTier **el Explorador de soluciones**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Crear la biblioteca de clases para albergar los TableAdapters (DataAccessTier)
 El paso siguiente después de crear el proyecto DataEntityTier consiste en crear otro proyecto de biblioteca de clases. Este proyecto contiene las clases TableAdapter generadas y se llama a la *nivel data access* de la aplicación. El nivel de acceso a datos contiene la información que se requiere para conectarse a la base de datos, y se encuentra normalmente en el nivel intermedio.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Para crear una biblioteca de clases independiente para los TableAdapters

1.  Haga doble clic en la solución en **el Explorador de soluciones** y elija **agregar** > **nuevo proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, en el panel central, seleccione **biblioteca de clases**.

3.  Denomine el proyecto **DataAccessTier** y elija **Aceptar**.

     Se crea el proyecto DataAccessTier y se agrega a la solución NTierWalkthrough.

## <a name="create-the-dataset"></a>Crear el conjunto de datos
 El paso siguiente consiste en crear un conjunto de datos con tipo. Objetos DataSet con tipo se crea con la clase de conjunto de datos (incluidos `DataTables` clases) y el `TableAdapter` clases en un solo proyecto. (Todas las clases se generan en un solo archivo.) Al separar el conjunto de datos y TableAdapters en proyectos diferentes, es la clase de conjunto de datos que se mueve a otro proyecto, dejando el `TableAdapter` clases en el proyecto original. Por lo tanto, cree el conjunto de datos en el proyecto que finalmente contendrá los TableAdapters (el proyecto DataAccessTier). Crear el conjunto de datos mediante el **Asistente para configuración de origen de datos**.

> [!NOTE]
> Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Para crear el conjunto de datos

1.  Seleccione el **DataAccessTier** en **el Explorador de soluciones**.

2.  En el **datos** menú, seleccione **Mostrar orígenes de datos**.

3.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.

4.  En el **elegir un tipo de origen de datos** página, seleccione **base de datos** y, a continuación, seleccione **siguiente**.

5.  En el **elegir la conexión de datos** , realice una de las acciones siguientes:

     Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

     O bien

     Seleccione **nueva conexión** para abrir el **Agregar conexión** cuadro de diálogo.

6.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, elija **siguiente**.

    > [!NOTE]
    > Si ha seleccionado un archivo de base de datos local (en lugar de conectarse a SQL Server), se le podría preguntar si desea agregar el archivo al proyecto. Elija **Sí** para agregar el archivo de base de datos al proyecto.

7.  Seleccione **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de aplicación** página.

8.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos** .

9.  Active las casillas de verificación de la **clientes** y **pedidos** tablas y, a continuación, elija **finalizar**.

     NorthwindDataSet se agrega al proyecto DataAccessTier y aparece en el **orígenes de datos** ventana.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Separar los TableAdapters del conjunto de datos
 Después de crear el conjunto de datos, separe la clase de conjunto de datos generada de los TableAdapters. Para ello, establezca el **DataSet Project** propiedad en el nombre del proyecto en el que se va a almacenar el separados por clase de conjunto de datos.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Para separar los TableAdapters del conjunto de datos

1. Haga doble clic en **NorthwindDataSet.xsd** en **el Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de Dataset**.

2. Seleccione un área vacía del diseñador.

3. Busque el **DataSet Project** nodo en el **propiedades** ventana.

4. En el **DataSet Project** lista, seleccione **DataEntityTier**.

5. En el menú **Compilar**, seleccione **Compilar solución**.

   El conjunto de datos y los TableAdapters se separan en los dos proyectos de biblioteca de clases. El proyecto que originalmente contenía el conjunto de datos completa (`DataAccessTier`) contiene ahora sólo los TableAdapters. El proyecto designado en el **DataSet Project** propiedad (`DataEntityTier`) contiene el conjunto de datos con tipo: *NorthwindDataSet.Dataset.Designer.vb* (o  *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Al separar conjuntos de datos y TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se trasladarán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

## <a name="create-a-new-service-application"></a>Cree una nueva aplicación de servicio
Este tutorial muestra cómo obtener acceso a la capa de acceso a datos mediante el uso de un servicio WCF, así que vamos a crear una nueva aplicación de servicio WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Para crear una nueva aplicación de servicio WCF

1.  Haga doble clic en la solución en **el Explorador de soluciones** y elija **agregar** > **nuevo proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo, seleccione **WCF**.  En el panel central, seleccione **biblioteca de servicios WCF**.

3.  Denomine el proyecto **DataService** y seleccione **Aceptar**.

     Se crea el proyecto DataService y se agrega a la solución NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Crear métodos en el nivel de acceso de datos para devolver los datos de clientes y pedidos
 El servicio de datos tiene que llamar a dos métodos en el nivel de acceso de datos: `GetCustomers` y `GetOrders`. Estos métodos devuelven Northwind `Customers` y `Orders` tablas. Crear el `GetCustomers` y `GetOrders` métodos en el `DataAccessTier` proyecto.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Customers

1.  En **el Explorador de soluciones**, haga doble clic en **NorthwindDataset.xsd** para abrir el conjunto de datos.

2.  Haga clic en **CustomersTableAdapter** y haga clic en **Agregar consulta**.

3.  En el **elegir un tipo de comando** página, deje el valor predeterminado de **usar instrucciones SQL** y haga clic en **siguiente**.

4.  En el **elegir un tipo de consulta** página, deje el valor predeterminado de **LECT que devuelve filas** y haga clic en **siguiente**.

5.  En el **especificar una instrucción SQL SELECT** página, deje la consulta predeterminada y haga clic en **siguiente**.

6.  En el **elija los métodos para generar** , escriba **GetCustomers** para el **nombre del método** en el **devolver un DataTable** sección.

7.  Haga clic en **Finalizar**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Orders

1.  Haga clic en **OrdersTableAdapter** y haga clic en **Agregar consulta**.

2.  En el **elegir un tipo de comando** página, deje el valor predeterminado de **usar instrucciones SQL** y haga clic en **siguiente**.

3.  En el **elegir un tipo de consulta** página, deje el valor predeterminado de **LECT que devuelve filas** y haga clic en **siguiente**.

4.  En el **especificar una instrucción SQL SELECT** página, deje la consulta predeterminada y haga clic en **siguiente**.

5.  En el **elija los métodos para generar** , escriba **GetOrders** para el **nombre del método** en el **devolver un DataTable** sección.

6.  Haga clic en **Finalizar**.

7.  En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Agregar una referencia a la entidad de datos y los niveles de acceso de datos al servicio de datos
 Dado que el servicio de datos requiere información del conjunto de datos y TableAdapters, agregue referencias a la **DataEntityTier** y **DataAccessTier** proyectos.

### <a name="to-add-references-to-the-data-service"></a>Para agregar referencias al servicio de datos

1.  Haga clic en **DataService** en **el Explorador de soluciones** y haga clic en **Agregar referencia**.

2.  Haga clic en el **proyectos** pestaña en el **Agregar referencia** cuadro de diálogo.

3.  Seleccione el **DataAccessTier** y **DataEntityTier** proyectos.

4.  Haga clic en **Aceptar**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Agregar funciones al servicio para llamar a los métodos GetCustomers y GetOrders en el nivel de acceso de datos
 Ahora que el nivel de acceso a datos contiene los métodos para devolver los datos, cree los métodos correspondientes en el servicio de datos para llamar a esos métodos del nivel de acceso a datos.

> [!NOTE]
> Para los proyectos de C#, deberá agregar una referencia al ensamblado `System.Data.DataSetExtensions` a fin de que el código siguiente pueda compilarse.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Para crear las funciones GetCustomers y GetOrders en el servicio de datos

1.  En el **DataService** del proyecto, haga doble clic en **IService1.vb** o **IService1.cs**.

2.  Agregue el siguiente código bajo el **agregue aquí sus operaciones de servicio** comentario:

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

3.  En el proyecto DataService, haga doble clic en **Service1.vb** (o **Service1.cs**).

4.  Agregue el código siguiente a la **Service1** clase:

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

5.  En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Crear un nivel de presentación para mostrar los datos del servicio de datos
 Ahora que la solución contiene el servicio de datos que tiene métodos que llaman a los datos de nivel de acceso a, cree otro proyecto que llama al servicio de datos y presentar los datos a los usuarios. Para este tutorial, cree una aplicación de Windows Forms; éste es el nivel de presentación de la aplicación con n niveles.

### <a name="to-create-the-presentation-tier-project"></a>Para crear el proyecto de nivel de presentación

1.  Haga doble clic en la solución en **el Explorador de soluciones** y elija **agregar** > **nuevo proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo, seleccione **Windows Desktop**. En el panel central, seleccione **aplicación de Windows Forms**.

3.  Denomine el proyecto **PresentationTier** y haga clic en **Aceptar**.

    Se crea el proyecto PresentationTier y se agrega a la solución NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Establecer el proyecto PresentationTier como proyecto de inicio
También estableceremos la **PresentationTier** proyecto para que sea el proyecto de inicio para la solución, porque es la aplicación cliente real que presenta e interactúa con los datos.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Para establecer el nuevo proyecto de nivel de presentación como proyecto de inicio

-   En **el Explorador de soluciones**, haga clic en **PresentationTier** y haga clic en **establecer como proyecto de inicio**.

## <a name="add-references-to-the-presentation-tier"></a>Agregar referencias al nivel de presentación
 La aplicación cliente PresentationTier requiere una referencia de servicio al servicio de datos con el fin de obtener acceso a los métodos en el servicio. Además, se requiere una referencia al conjunto de datos para que el servicio WCF pueda compartir los tipos. Hasta que habilite el tipo de uso compartido a través del servicio de datos, código agregado a la clase parcial del conjunto de datos no está disponible para el nivel de presentación. Como normalmente se agrega código, como el código de validación para la fila y columna, cambiar los eventos de una tabla de datos, es probable que quiera obtener acceso a este código desde el cliente.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Para agregar una referencia al nivel de presentación

1.  En **el Explorador de soluciones**, haga clic en **PresentationTier** y seleccione **Agregar referencia**.

2.  En el **Agregar referencia** cuadro de diálogo, seleccione el **proyectos** ficha.

3.  Seleccione **DataEntityTier** y elija **Aceptar**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Para agregar una referencia de servicio al nivel de presentación

1.  En **el Explorador de soluciones**, haga clic en **PresentationTier** y seleccione **Add Service Reference**.

2.  En el **Add Service Reference** cuadro de diálogo, seleccione **Discover**.

3.  Seleccione **Service1** y elija **Aceptar**.

    > [!NOTE]
    > Si tiene varios servicios en el equipo actual, seleccione el servicio que creó anteriormente en este tutorial (el servicio que contiene el `GetCustomers` y `GetOrders` métodos).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Agregar DataGridViews al formulario para mostrar los datos devueltos por el servicio de datos
 Después de agregar la referencia de servicio al servicio de datos, el **orígenes de datos** ventana se rellena automáticamente con los datos que es devuelto por el servicio.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Para agregar al formulario Windows Forms dos DataGridViews enlazados a datos 

1.  En **el Explorador de soluciones**, seleccione el **PresentationTier** proyecto.

2.  En el **orígenes de datos** ventana, expanda **NorthwindDataSet** y busque el **clientes** nodo.

3.  Arrastre el **clientes** nodo hasta Form1.

4.  En el **orígenes de datos** ventana, expanda el **clientes** nodo y busque relacionado **pedidos** nodo (el **pedidos** nodo anidado en el  **Los clientes** nodo).

5.  Arrastre el relacionados **pedidos** nodo hasta Form1.

6.  Cree un controlador de eventos para el evento `Form1_Load` haciendo doble clic sobre un área vacía del formulario.

7.  Agregue el código siguiente al controlador de eventos `Form1_Load`.

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Aumentar el tamaño de mensaje máximo permitido por el servicio
El valor predeterminado de `maxReceivedMessageSize` no es lo suficientemente grande como para contener los datos recuperados de la `Customers` y `Orders` tablas. En los pasos siguientes, deberá aumentar el valor por 6553600. Cambiar el valor en el cliente, que actualiza automáticamente la referencia de servicio.

> [!NOTE]
> El tamaño predeterminado más bajo está pensado para limitar la exposición a ataques por denegación de servicio (DOS). Para obtener más información, vea <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Para aumentar el valor de maxReceivedMessageSize

1.  En **el Explorador de soluciones**, haga doble clic en el **app.config** de archivos en el **PresentationTier** proyecto.

2.  Busque el **maxReceivedMessage** atributo de tamaño y cambie el valor a `6553600`.

## <a name="test-the-application"></a>Probar la aplicación
Ejecute la aplicación presionando **F5**. Los datos de la `Customers` y `Orders` tablas se recupera del servicio de datos y se muestra en el formulario.

## <a name="next-steps"></a>Pasos siguientes
 En función de los requisitos de la aplicación, hay varios pasos que es posible que desee realizar después de guardar los datos relacionados en la aplicación basada en Windows. Por ejemplo, a continuación se indican algunas de las mejoras que podría realizar en esta aplicación:

-   Agregar validación al conjunto de datos.

-   Agregar métodos adicionales al servicio para actualizar los datos de nuevo en la base de datos.

## <a name="see-also"></a>Vea también

- [Trabajar con conjuntos de datos en aplicaciones de n capas](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)