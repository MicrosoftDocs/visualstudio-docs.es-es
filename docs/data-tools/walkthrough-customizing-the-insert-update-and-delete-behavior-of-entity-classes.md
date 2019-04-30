---
title: 'Tutorial: Personalización del comportamiento de inserción, actualización y eliminación de clases de entidad'
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
ms.openlocfilehash: e869ae13c9d7ec82cb4d70fb5f3c5fce355691d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565412"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad

El [de LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona una superficie de diseño visual para crear y editar LINQ a las clases SQL (clases de entidad) que se basan en los objetos de una base de datos. Mediante el uso de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), puede usar la tecnología LINQ para las bases de datos SQL de acceso. Para más información, vea [LINQ (Language Integrated Query)](/dotnet/csharp/linq/).

De forma predeterminada, se proporciona la lógica para realizar actualizaciones por LINQ to SQL en tiempo de ejecución. El tiempo de ejecución crea de forma predeterminada `Insert`, `Update`, y `Delete` instrucciones según el esquema de la tabla (definiciones de columna e información de clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados. Para obtener más información, consulte [personalizar operaciones utilizando procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Este tutorial requiere la disponibilidad de los procedimientos almacenados **InsertCustomer**, **UpdateCustomer** y **DeleteCustomer** para la base de datos Northwind.

En este tutorial se proporcionan los pasos que se deben seguir para invalidar el comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL y volver a guardar los datos en una base de datos mediante procedimientos almacenados.

Durante este tutorial, aprenderá a realizar las siguientes tareas:

- Cree una nueva aplicación de Windows Forms y agregue un LINQ al archivo SQL a él.

- Crear una clase de entidad que se asigna a Northwind `Customers` tabla.

- Crear un origen de datos de objeto que hace referencia a LINQ to SQL `Customer` clase.

- Crear un formulario de Windows que contenga un <xref:System.Windows.Forms.DataGridView> que está enlazado a la `Customer` clase.

- Implementar la funcionalidad de guardar para el formulario.

- Crear <xref:System.Data.Linq.DataContext> los procedimientos almacenan de métodos agregando el **Object Relational Designer**.

- Configurar la `Customer` clase utilizar procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (**Explorador de objetos de SQL Server** se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el **instalador de Visual Studio**.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creación de una aplicación y adición de clases de LINQ to SQL

Dado que se trabaja con LINQ a las clases SQL y mostrar los datos en un formulario de Windows, cree una nueva aplicación de Windows Forms y agregue un LINQ al archivo de clases de SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Para crear un nuevo proyecto de aplicación de Windows Forms que contiene LINQ a las clases SQL

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **UpdatingWithSProcsWalkthrough**y, a continuación, elija **Aceptar**.

     Se crea el proyecto **UpdatingwithSProcsWalkthrough** y se agrega al **Explorador de soluciones**.

4. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

5. Haga clic en la plantilla **Clases de LINQ to SQL** y escriba **Northwind.dbml** en el cuadro **Nombre**.

6. Haga clic en **Agregar**.

     Un vacío archivo LINQ to SQL Classes (**Northwind.dbml**) se agrega al proyecto y el **Object Relational Designer** se abre.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Crear el origen de datos de clase y objeto de entidad de cliente

Creación de LINQ a las clases SQL que se asignan a las tablas de base de datos arrastrando las tablas del **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer**. El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos. Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para crear una clase de entidad Customer y configurar con ella un origen de datos

1. En **Explorador de servidores** o **Database Explorer**, busque el **cliente** tabla en la versión de SQL Server de la base de datos de ejemplo Northwind.

2. Arrastre el **clientes** nodo desde **Explorador de servidores** o **Database Explorer** en el **Object Relational Designer* superficie.

     Se crea una clase de entidad denominada **Customer**. Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers. La clase de entidad se denomina **Customer** (no **Customers**) porque representa a un único cliente de la tabla Customers.

    > [!NOTE]
    > Este comportamiento de cambio de nombre se denomina *pluralización*. Se puede activar o desactivar el [cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md). Para obtener más información, vea [Cómo: Activación y desactivación de la pluralización (Object Relational Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. En el menú **Compilar**, haga clic en **Generar UpdatingwithSProcsWalkthrough** para crear el proyecto.

4. Para abrir el **orígenes de datos** ventana, en el **datos** menú, haga clic en **Mostrar orígenes de datos**.

5. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

6. Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.

7. Expanda el nodo **UpdatingwithSProcsWalkthrough** y, después, busque y seleccione la clase **Customer**.

    > [!NOTE]
    > Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.
8. Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Crear un control DataGridView para mostrar los datos del cliente en un formulario de Windows

Crear controles enlazados a las clases de entidad arrastrando LINQ a elementos de origen de datos SQL desde el **orígenes de datos** ventana en un formulario de Windows.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para agregar controles enlazados a las clases de entidad

1. Abra **Form1** en la vista Diseño.

2. Desde la ventana **Orígenes de datos**, arrastre el nodo **Customer** hasta **Form1**.

    > [!NOTE]
    > Para mostrar la ventana **Orígenes de datos**, haga clic en **Mostrar orígenes de datos** en el menú **Datos**.

3. Abra **Form1** en el Editor de código.

4. Agregue el siguiente código al formulario, global para el formulario, fuera de cualquier método concreto, pero en el `Form1` clase:

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

De forma predeterminada, el botón Guardar no está habilitado y la funcionalidad de guardar no está implementada. Además, no se agrega automáticamente código para guardar los datos modificados en la base de datos cuando se crean controles enlazados a datos para los orígenes de datos de objeto. En esta sección se explica cómo habilitar el guardado botón e implementar funcionalidad de guardar para LINQ para objetos de SQL.

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

1. Abra el archivo LINQ to SQL en el **Object Relational Designer**. Haga doble clic en el archivo **Northwind.dbml** en el **Explorador de soluciones**.

2. En el **Explorador de servidores** o **Explorador de bases de datos**, expanda el nodo **Procedimientos almacenados** de las bases de datos Northwind y busque los procedimientos almacenados **InsertCustomers**, **UpdateCustomers** y **DeleteCustomers**.

3. Arrastre los tres procedimientos almacenados en el **Object Relational Designer**.

     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Seleccione el **cliente** clase de entidad en el **Object Relational Designer**.

5. En la ventana **Propiedades**, seleccione la propiedad **Insertar**.

6. Haga clic en los puntos suspensivos (**...**) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.

7. Seleccione **Personalizar**.

8. Seleccione el método **InsertCustomers** en la lista **Personalizar**.

9. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.

    > [!NOTE]
    > Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic **aplicar**, que proporciona una oportunidad para aplicar cualquier cambio aparece un cuadro de diálogo de advertencia.

10. Seleccione **Actualizar** en la lista **Comportamiento**.

11. Seleccione **Personalizar**.

12. Seleccione el método **UpdateCustomers** en la lista **Personalizar**.

     Examine la lista de **Argumentos de método** y **Propiedades de clase**, y observe que hay dos **argumentos de método** y dos **propiedades de clase** para algunas columnas de la tabla. De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.

13. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)**.

    > [!NOTE]
    > De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan. Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el **Object Relational Designer** no puede determinar la asignación correcta. Además, si los argumentos de método no tienen propiedades de clase válidas a las que asignarse, puede establecer el valor de **Propiedades de clase** en **(Ninguno)**.

14. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.

15. Seleccione **Eliminar** en la lista **Comportamiento**.

16. Seleccione **Personalizar**.

17. Seleccione el método **DeleteCustomers** en la lista **Personalizar**.

18. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)**.

19. Haga clic en **Aceptar**.

> [!NOTE]
> Aunque no es un problema de este tutorial particular, es importante destacar que LINQ to SQL controla valores base de datos generados automáticamente para la identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y las columnas de marca de tiempo durante las inserciones y actualizaciones. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por base de datos, debe establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> a `true` y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> a uno de los siguientes: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), o [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

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

Dependiendo de los requisitos de la aplicación, hay varios pasos que desee realizar después de crear LINQ a las clases de entity SQL. Entre las mejoras que podría realizar a esta aplicación se incluyen:

- Implementar la comprobación de simultaneidad durante las actualizaciones. Para obtener información, consulte [simultaneidad optimista: información general sobre](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Agregar consultas LINQ para filtrar los datos. Para obtener información, consulte [Introducción a las consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [DataContext (métodos)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Consultas de LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)