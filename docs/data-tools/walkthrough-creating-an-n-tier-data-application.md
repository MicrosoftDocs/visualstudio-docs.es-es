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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a88f0382a93027cc952dfe44f0027e6ab1076a45
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916495"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Tutorial: crear una aplicación de datos de n niveles
Las aplicaciones de datos con *n niveles* son aplicaciones que acceden a datos y que están separadas en varias capas lógicas o *niveles*. Al separar los componentes de la aplicación en estos niveles individuales, se aumenta la facilidad de mantenimiento y la escalabilidad de la aplicación. Esto se consigue mediante una integración más sencilla de nuevas tecnologías, que se pueden aplicar a un solo nivel sin necesidad de volver a diseñar la solución completa. Una arquitectura típica con n niveles incluye un nivel de presentación, un nivel intermedio y una capa de datos. El nivel intermedio incluye normalmente una capa de acceso a datos, una capa de la lógica empresarial y componentes compartidos, tales como autenticación y validación. La capa de datos incluye una base de datos relacional. Las aplicaciones con n niveles normalmente almacenan la información confidencial en la capa de acceso a datos del nivel intermedio para aislar esa información de los usuarios finales que obtienen acceso al nivel de presentación. Para obtener más información, vea [información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).

Una manera de separar los distintos niveles de una aplicación con n niveles consiste en crear proyectos independientes para cada nivel que se desee incluir en la aplicación. Los conjuntos de datos con tipo contienen una propiedad `DataSet Project` que determina en qué proyectos deben ir el conjunto de datos y el código de `TableAdapter` generados.

Este tutorial muestra cómo separar el código de conjunto de datos y `TableAdapter` en proyectos de bibliotecas de clases individuales mediante el **Diseñador de DataSet**. Después de separar el conjunto de datos y el código de TableAdapter, cree una [Windows Communication Foundation servicios y WCF Data Services en el servicio de Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) para llamar al nivel de acceso a datos. Por último, cree una aplicación Windows Forms como el nivel de presentación. Este nivel obtiene acceso a los datos desde el servicio de datos.

Durante este tutorial, realizará los pasos siguientes:

- Cree una nueva solución de n niveles que contenga varios proyectos.

- Agregar dos proyectos de bibliotecas de clases a la solución con n niveles.

- Cree un conjunto de datos con tipo mediante el **Asistente para configuración de orígenes de datos**.

- Separe los [TableAdapters](create-and-configure-tableadapters.md) y el código de conjunto de datos generados en proyectos discretos.

- Crear un servicio de Windows Communication Foundation (WCF) para realizar llamadas al nivel de acceso a datos.

- Crear funciones en el servicio para recuperar datos del nivel de acceso a datos.

- Crear una aplicación de Windows Forms que actúe como nivel de presentación.

- Crear controles de formularios Windows Forms enlazados al origen de datos.

- Escribir código para rellenar las tablas de datos.

![vínculo a vídeo](../data-tools/media/playvideo.gif) para una versión en vídeo de este tema, consulte [vídeo sobre cómo: Crear una aplicación de datos de n niveles](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Requisitos previos
En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **desarrollo de escritorio de .net** o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (**Explorador de objetos de SQL Server** se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Crear la solución de n niveles y la biblioteca de clases para contener el conjunto de DataSet (DataEntityTier)
El primer paso de este tutorial consiste en crear una solución y dos proyectos de biblioteca de clases. La primera biblioteca de clases contiene el conjunto de datos (la clase `DataSet` con tipo generada y DataTables que contienen los datos de la aplicación). Este proyecto se utiliza como la capa de entidad de datos de la aplicación, y se ubica normalmente en el nivel intermedio. El conjunto de DataSet crea el conjunto de código inicial y lo separa automáticamente en las dos bibliotecas de clases.

> [!NOTE]
> Asegúrese de asignar el nombre correcto al proyecto y a la solución antes de hacer clic en **Aceptar**. De este modo, será más fácil poder completar este tutorial.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Para crear la solución con n niveles y la biblioteca de clases DataEntityTier

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#**  o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **biblioteca de clases** .

4. Asigne al proyecto el nombre **DataEntityTier**.

5. Asigne a la solución el nombre **NTierWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea una solución NTierWalkthrough que contiene el proyecto DataEntityTier y se agrega al **Explorador de soluciones**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Crear la biblioteca de clases para contener los TableAdapters (DataAccessTier)
El paso siguiente después de crear el proyecto DataEntityTier consiste en crear otro proyecto de biblioteca de clases. Este proyecto contiene los TableAdapters generados y se denomina *nivel de acceso a datos* de la aplicación. El nivel de acceso a datos contiene la información que se requiere para conectarse a la base de datos, y se encuentra normalmente en el nivel intermedio.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Para crear una biblioteca de clases independiente para los TableAdapters

1. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , en el panel central, seleccione **biblioteca de clases**.

3. Asigne al proyecto el nombre **DataAccessTier** y elija **Aceptar**.

     Se crea el proyecto DataAccessTier y se agrega a la solución NTierWalkthrough.

## <a name="create-the-dataset"></a>Crear el conjunto de
El paso siguiente consiste en crear un conjunto de datos con tipo. Los conjuntos de valores de tipos se crean con la clase DataSet (incluidas las clases `DataTables`) y las clases `TableAdapter` en un solo proyecto. (Todas las clases se generan en un solo archivo). Al separar el conjunto de objetos y los TableAdapters en proyectos diferentes, es la clase de conjunto de DataSet que se mueve al otro proyecto, y se dejan las clases de `TableAdapter` en el proyecto original. Por lo tanto, cree el conjunto de objetos en el proyecto que contendrá en última instancia los TableAdapters (el proyecto DataAccessTier). Puede crear el conjunto de datos mediante el **Asistente para la configuración de orígenes de datos**.

> [!NOTE]
> Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases](../data-tools/installing-database-systems-tools-and-samples.md)de datos de ejemplo.

### <a name="to-create-the-dataset"></a>Para crear el conjunto de datos

1. Seleccione **DataAccessTier** en **Explorador de soluciones**.

2. En el menú **datos** , seleccione **Mostrar orígenes de datos**.

   Se abre la ventana **Orígenes de datos**.

3. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

4. En la página **elegir un tipo de origen de datos** , seleccione **base** de datos y, a continuación, seleccione **siguiente**.

5. En la página **Elegir la conexión de datos**, realice una de las siguientes acciones:

     Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

     O bien,

     Seleccione **nueva conexión** para abrir el cuadro de diálogo **Agregar conexión** .

6. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, elija **siguiente**.

    > [!NOTE]
    > Si ha seleccionado un archivo de base de datos local (en lugar de conectarse a SQL Server), se le podría preguntar si desea agregar el archivo al proyecto. Elija **sí** para agregar el archivo de base de datos al proyecto.

7. Seleccione **siguiente** en la página **guardar la cadena de conexión en el archivo de configuración de la aplicación** .

8. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos** .

9. Active las casillas de las tablas **Customers** y **Orders** y, a continuación, elija **Finalizar**.

     NorthwindDataSet se agrega al proyecto DataAccessTier y aparece en la ventana **Orígenes de datos**.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Separar los TableAdapters del conjunto de objetos
Después de crear el conjunto de datos, separe la clase de conjunto de datos generada de los TableAdapters. Esto se hace configurando la propiedad **DataSet Project** con el nombre del proyecto en el que se va a almacenar la clase de conjunto de datos separada.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Para separar los TableAdapters del conjunto de datos

1. Haga doble clic en **NorthwindDataSet.xsd** en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.

2. Seleccione un área vacía en el diseñador.

3. Busque el nodo **DataSet Project** en la ventana **Propiedades**.

4. En la lista **conjunto de proyectos** , seleccione **DataEntityTier**.

5. En el menú **Compilar**, seleccione **Compilar solución**.

   El conjunto de datos y los TableAdapters se separan en los dos proyectos de biblioteca de clases. El proyecto que contenía originalmente todo el conjunto de objetos (`DataAccessTier`) contiene ahora solo los TableAdapters. El proyecto designado en la propiedad **DataSet Project** (`DataEntityTier`) contiene el DataSet con tipo: *NorthwindDataSet. DataSet. Designer. vb* (o *NorthwindDataSet.DataSet.Designer.CS*).

> [!NOTE]
> Cuando los conjuntos de datos se separan de los TableAdapters (estableciendo la propiedad **DataSet Project**), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.

## <a name="create-a-new-service-application"></a>Crear una nueva aplicación de servicio
En este tutorial se muestra cómo obtener acceso al nivel de acceso a datos mediante un servicio WCF, así que vamos a crear una nueva aplicación de servicio WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Para crear una nueva aplicación de servicio WCF

1. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , en el panel izquierdo, seleccione **WCF**. En el panel central, seleccione **biblioteca de servicios WCF**.

3. Asigne **al proyecto el** nombre y seleccione **Aceptar**.

     Se crea el proyecto DataService y se agrega a la solución NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Crear métodos en el nivel de acceso a datos para devolver los datos de los clientes y pedidos
El servicio de datos tiene que llamar a dos métodos en el nivel de acceso a datos: `GetCustomers` y `GetOrders`. Estos métodos devuelven las tablas `Customers` y `Orders` de Northwind. Cree los métodos `GetCustomers` y `GetOrders` en el proyecto de `DataAccessTier`.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Customers

1. En **Explorador de soluciones**, haga doble clic en **NorthwindDataSet. xsd** para abrir el conjunto de DataSet.

2. Haga clic con el botón secundario en **CustomersTableAdapter** y haga clic en **Agregar consulta**.

3. En la página **Elija un tipo de comando**, deje el valor predeterminado **Usar instrucciones SQL** y haga clic en **Siguiente**.

4. En la página **Elija un tipo de consulta**, deje el valor predeterminado **SELECT que devuelve filas** y haga clic en **Siguiente**.

5. En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.

6. En la página **Elija los métodos que se van a generar**, escriba **GetCustomers** como **Nombre del método** en la sección **Devolver un DataTable**.

7. Haga clic en **Finalizar**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Para crear un método en el nivel de acceso a datos que devuelva la tabla Orders

1. Haga clic con el botón derecho en **OrdersTableAdapter** y elija **Agregar consulta**.

2. En la página **Elija un tipo de comando**, deje el valor predeterminado **Usar instrucciones SQL** y haga clic en **Siguiente**.

3. En la página **Elija un tipo de consulta**, deje el valor predeterminado **SELECT que devuelve filas** y haga clic en **Siguiente**.

4. En la página **Especifique una instrucción SELECT de SQL**, deje la consulta predeterminada y haga clic en **Siguiente**.

5. En la página **Elija los métodos que se van a generar**, escriba **GetOrders** como **Nombre del método** en la sección **Devolver un DataTable**.

6. Haga clic en **Finalizar**.

7. En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Agregar una referencia a los niveles de entidad de datos y de acceso a datos al servicio de datos
Dado que el servicio de datos requiere información del conjunto de datos y los TableAdapters, agregue referencias a los proyectos **DataEntityTier** y **DataAccessTier**.

### <a name="to-add-references-to-the-data-service"></a>Para agregar referencias al servicio de datos

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **DataService** y después haga clic en **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos**.

3. Seleccione los proyectos **DataAccessTier** y **DataEntityTier**.

4. Haga clic en **Aceptar**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Agregar funciones al servicio para llamar a los métodos GetCustomers y GetOrders en el nivel de acceso a datos
Ahora que el nivel de acceso a datos contiene los métodos para devolver los datos, cree los métodos correspondientes en el servicio de datos para llamar a esos métodos del nivel de acceso a datos.

> [!NOTE]
> Para los proyectos de C#, deberá agregar una referencia al ensamblado `System.Data.DataSetExtensions` a fin de que el código siguiente pueda compilarse.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Para crear las funciones GetCustomers y GetOrders en el servicio de datos

1. En el proyecto **DataService**, haga doble clic en **IService1.vb** o **IService1.cs**.

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

3. En el proyecto DataService, haga doble clic en **Service1.vb** (o en **Service1.cs**).

4. Agregue el código siguiente a la clase **Service1**:

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

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Crear un nivel de presentación para Mostrar datos del servicio de datos
Ahora que la solución contiene el servicio de datos que tiene métodos, que llaman al nivel de acceso a datos, cree otro proyecto que llame al servicio de datos y presente los datos a los usuarios. Para este tutorial, cree una aplicación de formularios Windows Forms; éste es el nivel de presentación de la aplicación con n niveles.

### <a name="to-create-the-presentation-tier-project"></a>Para crear el proyecto de nivel de presentación

1. Haga clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , en el panel izquierdo, seleccione **escritorio de Windows**. En el panel central, seleccione **Windows Forms aplicación**.

3. Denomine el proyecto **PresentationTier** y haga clic en **Aceptar**.

    Se crea el proyecto PresentationTier y se agrega a la solución NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Establecer el proyecto PresentationTier como proyecto de inicio
Estableceremos el proyecto **PresentationTier** en el proyecto de inicio de la solución, ya que es la aplicación cliente real que presenta e interactúa con los datos.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Para establecer el nuevo proyecto de nivel de presentación como proyecto de inicio

- En el **Explorador de soluciones**, haga clic con el botón derecho en **PresentationTier** y después haga clic en **Establecer como proyecto de inicio**.

## <a name="add-references-to-the-presentation-tier"></a>Agregar referencias al nivel de presentación
La aplicación cliente PresentationTier requiere una referencia de servicio al servicio de datos para poder acceder a los métodos del servicio. Además, se requiere una referencia al conjunto de datos para que el servicio WCF pueda compartir los tipos. Hasta que habilite el uso compartido de tipos a través del servicio de datos, el código agregado a la clase de conjunto de datos parcial no estará disponible en el nivel de presentación. Dado que normalmente agrega código, como código de validación, a los eventos de cambio de filas y columnas de una tabla de datos, es probable que desee tener acceso a este código desde el cliente.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Para agregar una referencia al nivel de presentación

1. En **Explorador de soluciones**, haga clic con el botón secundario en **PresentationTier** y seleccione **Agregar referencia**.

2. En el cuadro de diálogo **Agregar referencia** , seleccione la pestaña **proyectos** .

3. Seleccione **DataEntityTier** y elija **Aceptar**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Para agregar una referencia de servicio al nivel de presentación

1. En **Explorador de soluciones**, haga clic con el botón secundario en **PresentationTier** y seleccione **Agregar referencia de servicio**.

2. En el cuadro de diálogo **Agregar referencia de servicio** , seleccione **detectar**.

3. Seleccione **Service1** y elija **Aceptar**.

    > [!NOTE]
    > Si tiene varios servicios en el equipo actual, seleccione el servicio que creó anteriormente en este tutorial (el servicio que contiene los métodos `GetCustomers` y `GetOrders`).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Agregar DataGridViews al formulario para mostrar los datos devueltos por el servicio de datos
Después de agregar la referencia de servicio al servicio de datos, la ventana **Orígenes de datos** se rellena automáticamente con los datos devueltos por el servicio.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Para agregar al formulario Windows Forms dos DataGridViews enlazados a datos

1. En el **Explorador de soluciones**, seleccione el proyecto **PresentationTier**.

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Aumentar el tamaño de mensaje máximo permitido por el servicio
El valor predeterminado de `maxReceivedMessageSize` no es lo suficientemente grande como para contener los datos recuperados de las tablas `Customers` y `Orders`. En los pasos siguientes, aumentará el valor a 6553600. El valor se cambia en el cliente, que actualiza automáticamente la referencia de servicio.

> [!NOTE]
> El tamaño predeterminado más bajo está pensado para limitar la exposición a ataques por denegación de servicio (DOS). Para obtener más información, vea <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Para aumentar el valor de maxReceivedMessageSize

1. En el **Explorador de soluciones**, haga doble clic en el archivo **app.config** del proyecto **PresentationTier**.

2. Busque el atributo de tamaño **maxReceivedMessage** y cambie su valor a `6553600`.

## <a name="test-the-application"></a>Probar la aplicación
Ejecute la aplicación presionando **F5**. Los datos de las tablas `Customers` y `Orders` se recuperan del servicio de datos y se muestran en el formulario.

## <a name="next-steps"></a>Pasos siguientes
En función de los requisitos de la aplicación, hay varios pasos que es posible que desee realizar después de guardar los datos relacionados en la aplicación basada en Windows. Por ejemplo, a continuación se indican algunas de las mejoras que podría realizar en esta aplicación:

- Agregar validación al conjunto de datos.

- Agregar métodos adicionales al servicio para actualizar los datos de nuevo en la base de datos.

## <a name="see-also"></a>Vea también

- [Trabajar con conjuntos de datos en aplicaciones de n capas](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
