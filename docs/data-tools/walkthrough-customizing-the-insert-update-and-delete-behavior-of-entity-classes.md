---
title: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb6bbde145317d737afdbf819dba8ee53f805f72
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252976"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad

[En las herramientas de LINQ to SQL de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) se proporciona una superficie de diseño visual para crear y editar clases de LINQ to SQL (clases de entidad) basadas en objetos de una base de datos. Con [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), puede usar la tecnología LINQ para tener acceso a las bases de datos SQL. Para más información, vea [LINQ (Language Integrated Query)](/dotnet/csharp/linq/).

De forma predeterminada, el tiempo de ejecución de LINQ to SQL proporciona la lógica para realizar actualizaciones. El tiempo de ejecución `Insert`crea `Update`las instrucciones `Delete` , y predeterminadas basadas en el esquema de la tabla (las definiciones de columna y la información de clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados. Para obtener más información, vea [personalizar las operaciones mediante procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Este tutorial requiere la disponibilidad de los procedimientos almacenados **InsertCustomer**, **UpdateCustomer** y **DeleteCustomer** para la base de datos Northwind.

En este tutorial se proporcionan los pasos que debe seguir para invalidar el comportamiento predeterminado LINQ to SQL en tiempo de ejecución para guardar los datos de nuevo en una base de datos mediante procedimientos almacenados.

Durante este tutorial, aprenderá a realizar las siguientes tareas:

- Cree una nueva aplicación de Windows Forms y agréguele un archivo de LINQ to SQL.

- Cree una clase de entidad asignada a la tabla `Customers` Northwind.

- Cree un origen de datos de objeto que haga `Customer` referencia a la clase LINQ to SQL.

- Cree un formulario de Windows Forms <xref:System.Windows.Forms.DataGridView> que contenga un que `Customer` esté enlazado a la clase.

- Implementar la funcionalidad de guardar para el formulario.

- Cree <xref:System.Data.Linq.DataContext> métodos agregando procedimientos almacenados a Object Relational **Designer**.

- Configure `Customer` la clase para que use procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (**Explorador de objetos de SQL Server** se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el **instalador de Visual Studio**). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creación de una aplicación y adición de clases de LINQ to SQL

Dado que está trabajando con clases de LINQ to SQL y muestra los datos en un Windows Form, cree una nueva aplicación de Windows Forms y agregue un archivo de clases de LINQ to SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Para crear un nuevo proyecto de aplicación de Windows Forms que contenga clases de LINQ to SQL

1. En Visual Studio, en el menú **archivo** , seleccione **nuevo** > **proyecto**.

2. Expanda **Visual C#**  o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **UpdatingWithSProcsWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea el proyecto **UpdatingwithSProcsWalkthrough** y se agrega al **Explorador de soluciones**.

4. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

5. Haga clic en la plantilla **Clases de LINQ to SQL** y escriba **Northwind.dbml** en el cuadro **Nombre**.

6. Haga clic en **Agregar**.

     Se agrega al proyecto un archivo de clases de LINQ to SQL vacío (**Northwind. dbml**) y se abre **o/R Designer** .

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Crear la clase de entidad Customer y el origen de datos de objeto

Cree LINQ to SQL clases que se asignan a tablas de base de datos arrastrando las tablas de **Explorador de servidores** o **Explorador de bases de datos** a Object Relational **Designer**. El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos. Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para crear una clase de entidad Customer y configurar con ella un origen de datos

1. En **Explorador de servidores** o **Explorador de bases de datos**, busque la tabla **Customer** en la versión SQL Server de la base de datos de ejemplo Northwind.

2. Arrastre el nodo **Customers** desde **Explorador de servidores** o **Explorador de bases de datos** a la superficie de Object Relational*Designer* .

     Se crea una clase de entidad denominada **Customer**. Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers. La clase de entidad se denomina **Customer** (no **Customers**) porque representa a un único cliente de la tabla Customers.

    > [!NOTE]
    > Este comportamiento de cambio de nombre se denomina *pluralización*. Se puede activar o desactivar en el cuadro de [diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md). Para obtener más información, vea [Cómo: Activación y desactivación de la pluralización (Object Relational Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. En el menú **Compilar**, haga clic en **Generar UpdatingwithSProcsWalkthrough** para crear el proyecto.

4. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

5. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

6. Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.

7. Expanda el nodo **UpdatingwithSProcsWalkthrough** y, después, busque y seleccione la clase **Customer**.

    > [!NOTE]
    > Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.
8. Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Crear un DataGridView para mostrar los datos del cliente en Windows Forms

Cree controles enlazados a las clases de entidad arrastrando LINQ to SQL elementos de origen de datos desde la ventana **orígenes de datos** hasta un formulario Windows Forms.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para agregar controles enlazados a las clases de entidad

1. Abra **Form1** en la vista Diseño.

2. Desde la ventana **Orígenes de datos**, arrastre el nodo **Customer** hasta **Form1**.

    > [!NOTE]
    > Para mostrar la ventana **Orígenes de datos**, haga clic en **Mostrar orígenes de datos** en el menú **Datos**.

3. Abra **Form1** en el Editor de código.

4. Agregue el código siguiente al formulario, global al formulario, fuera de cualquier método específico, pero dentro de la `Form1` clase:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Cree un controlador de eventos para el evento `Form_Load` y agregue el código siguiente al controlador:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implementar la funcionalidad de guardar

De forma predeterminada, el botón Guardar no está habilitado y la funcionalidad de guardar no está implementada. Además, no se agrega automáticamente código para guardar los datos modificados en la base de datos cuando se crean controles enlazados a datos para los orígenes de datos de objeto. En esta sección se explica cómo habilitar el botón guardar e implementar la funcionalidad de guardar para los objetos de LINQ to SQL.

### <a name="to-implement-save-functionality"></a>Para implementar la funcionalidad de guardar

1. Abra **Form1** en la vista Diseño.

2. Seleccione el botón Guardar en **CustomersBindingNavigator** (el botón con el icono del disquete).

3. En la ventana **Propiedades**, establezca la propiedad **Enabled** en **True**.

4. Haga doble clic en el botón Guardar para crear un controlador de eventos y cambiar al Editor de código.

5. Agregue el código siguiente al controlador de eventos del botón Guardar:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Invalidar el comportamiento predeterminado para realizar actualizaciones (inserciones, actualizaciones y eliminaciones)

### <a name="to-override-the-default-update-behavior"></a>Para invalidar el comportamiento de actualización predeterminado

1. Abra el archivo LINQ to SQL en Object Relational **Designer**. Haga doble clic en el archivo **Northwind.dbml** en el **Explorador de soluciones**.

2. En el **Explorador de servidores** o **Explorador de bases de datos**, expanda el nodo **Procedimientos almacenados** de las bases de datos Northwind y busque los procedimientos almacenados **InsertCustomers**, **UpdateCustomers** y **DeleteCustomers**.

3. Arrastre los tres procedimientos almacenados hasta Object Relational **Designer**.

     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

4. Seleccione la clase de entidad **Customer** en **Object**Relational Designer.

5. En la ventana **Propiedades**, seleccione la propiedad **Insertar**.

6. Haga clic en los puntos suspensivos ( **...** ) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.

7. Seleccione **Personalizar**.

8. Seleccione el método **InsertCustomers** en la lista **Personalizar**.

9. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.

    > [!NOTE]
    > Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic en **aplicar**, aparece un cuadro de diálogo de advertencia que proporciona la oportunidad de aplicar los cambios.

10. Seleccione **Actualizar** en la lista **Comportamiento**.

11. Seleccione **Personalizar**.

12. Seleccione el método **UpdateCustomers** en la lista **Personalizar**.

     Examine la lista de **Argumentos de método** y **Propiedades de clase**, y observe que hay dos **argumentos de método** y dos **propiedades de clase** para algunas columnas de la tabla. De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.

13. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)** .

    > [!NOTE]
    > De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan. Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el **Object Relational Designer** no puede determinar la asignación correcta. Además, si los argumentos de método no tienen propiedades de clase válidas a las que asignarse, puede establecer el valor de **Propiedades de clase** en **(Ninguno)** .

14. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.

15. Seleccione **Eliminar** en la lista **Comportamiento**.

16. Seleccione **Personalizar**.

17. Seleccione el método **DeleteCustomers** en la lista **Personalizar**.

18. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)** .

19. Haga clic en **Aceptar**.

> [!NOTE]
> Aunque no es un problema para este tutorial concreto, merece la pena tener en cuenta que LINQ to SQL controla automáticamente los valores generados por la base de datos para la identidad (incremento automático), ROWGUIDCOL (GUID generado por la base de datos) y las columnas timestamp durante las inserciones. actualizaciones. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> debe `true` establecer <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> manualmente en y en uno de los siguientes elementos: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. alinserte](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)o [AutoSync. actualizar](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Probar la aplicación

Vuelva a ejecutar la aplicación para comprobar que el procedimiento almacenado **UpdateCustomers** actualiza correctamente el registro de cliente en la base de datos.

1. Presione **F5**.

2. Modifique un registro en la cuadrícula para probar el comportamiento de actualización.

3. Agregue un nuevo registro para probar el comportamiento de inserción.

4. Haga clic en el botón Guardar para volver a guardar los cambios en la base de datos.

5. Cierre el formulario.

6. Presione **F5** y compruebe que se conservan el registro actualizado y el registro que se acaba de insertar.

7. Elimine el nuevo registro creado en el paso 3 para probar el comportamiento de eliminación.

8. Haga clic en el botón Guardar para enviar los cambios y quitar el registro eliminado de la base de datos.

9. Cierre el formulario.

10. Presione **F5** y compruebe que el registro eliminado se quitó de la base de datos.

    > [!NOTE]
    > Si la aplicación usa SQL Server Express Edition, dependiendo del valor de la propiedad **Copiar en el directorio de resultados** del archivo de base de datos, puede que los cambios no aparezcan al presionar **F5** en el paso 10.

## <a name="next-steps"></a>Pasos siguientes

En función de los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear LINQ to SQL clases de entidad. Entre las mejoras que podría realizar a esta aplicación se incluyen:

- Implementar la comprobación de simultaneidad durante las actualizaciones. Para obtener información, consulte [simultaneidad optimista: información general](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Agregar consultas LINQ para filtrar los datos. Para obtener información, consulte [Introduction to LINQC#queries ()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [DataContext (métodos)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Consultas de LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)