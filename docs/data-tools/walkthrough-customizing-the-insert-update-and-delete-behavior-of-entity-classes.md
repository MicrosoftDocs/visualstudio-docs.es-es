---
title: "Tutorial: Personalizar la instrucción insert, update y delete de comportamiento de las clases de entidad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f711c0fcdd4866a1b097585052cdcb3733e426d8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Tutorial: Personalizar la instrucción insert, update y delete de comportamiento de las clases de entidad
El [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona una superficie de diseño visual para crear y editar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] clases (las clases de entidad) que se basan en los objetos de una base de datos. Mediante el uso de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), puede utilizar la tecnología LINQ a las bases de datos SQL de acceso. Para más información, consulte [LINQ (Language Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
El motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] proporciona, de forma predeterminada, la lógica para realizar actualizaciones. El motor en tiempo de ejecución crea las instrucciones predeterminadas de inserción, actualización y eliminación basándose en el esquema de la tabla (definiciones de columna e información de la clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados. Para obtener más información, consulte [personalizar operaciones utilizando procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).  
  
> [!NOTE]
>  Este tutorial requiere la disponibilidad de la **InsertCustomer**, **UpdateCustomer**, y **DeleteCustomer** procedimientos almacenados para la base de datos Northwind.  
  
En este tutorial se proporcionan los pasos que se deben seguir para invalidar el comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL y volver a guardar los datos en una base de datos mediante procedimientos almacenados.  
  
Durante este tutorial, aprenderá a realizar las siguientes tareas:  
  
-   Crear una nueva aplicación de Windows Forms y agregarle un archivo de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
-   Crear una clase de entidad asignada a la tabla Customers de Northwind.  
  
-   Crear un origen de datos de objeto que haga referencia a la clase Customer de LINQ to SQL.  
  
-   Crear un formulario Windows Forms con un control <xref:System.Windows.Forms.DataGridView> enlazado a la clase Customer.  
  
-   Implementar la funcionalidad de guardar para el formulario.  
  
-   Crear los métodos de <xref:System.Data.Linq.DataContext> agregando procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configurar la clase Customer de modo que se usen los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones.  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.  
  
1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.  
  
2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:  

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .  

       Se abre una ventana del editor de consultas.  

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.  

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.  

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Crear una aplicación y agregar clases de LINQ to SQL  
Dado que va a trabajar con clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] y mostrar los datos en un Windows Form, cree una nueva aplicación de Windows Forms y agregue un archivo de clases de LINQ to SQL.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Para crear un nuevo proyecto de aplicación de Windows Forms que contiene LINQ a las clases SQL  
  
1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .  
  
2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.  

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.  

4. Denomine el proyecto **UpdatingWithSProcsWalkthrough**y, a continuación, elija **Aceptar**. 
  
     El **UpdatingWithSProcsWalkthrough** proyecto se crea y se agrega a **el Explorador de soluciones**.  
  
4.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
5.  Haga clic en el **clases LINQ to SQL** plantilla y escriba **Northwind.dbml** en el **nombre** cuadro.  
  
6.  Haga clic en **Agregar**.  
  
     Se agrega al proyecto un archivo de clases de LINQ to SQL vacío (Northwind.dbml) y se abre el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Crear la clase de entidad Customer y el origen de datos de objeto  
 Crear [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] las clases que se asignan a tablas de base de datos arrastrando las tablas de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos. Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para crear una clase de entidad Customer y configurar con ella un origen de datos  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, busque la tabla Customer en la versión de SQL Server de la base de datos de ejemplo Northwind. 
  
2.  Arrastre el **clientes** nodo desde **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] superficie.  
  
     Una clase de entidad denominada **cliente** se crea. Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers. La clase de entidad se denomina **cliente** (no **clientes**) porque representa un único cliente de la tabla Customers.  
  
    > [!NOTE]
    >  Este comportamiento de cambio de nombre se denomina *pluralización*. Se puede activar o desactivar el [cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md). Para obtener más información, consulte [Cómo: activar y desactivar (Object Relational Designer) pluralización](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  En el **generar** menú, haga clic en **generar UpdatingwithSProcsWalkthrough** para compilar el proyecto.  
  
4.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
5.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
6.  Haga clic en **objeto** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.  
  
7.  Expanda el **UpdatingwithSProcsWalkthrough** nodo y busque y seleccione el **cliente** clase.  
  
    > [!NOTE]
    >  Si el **cliente** clase no está disponible, cancele el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
8.  Haga clic en **finalizar** para crear el origen de datos y agregar el **cliente** clase de entidad para el **orígenes de datos** ventana.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Crear un control DataGridView para mostrar los datos del cliente en un formulario Windows Forms  
 Crear controles que están enlazados a las clases de entidad arrastrando [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] elementos de origen de datos la **orígenes de datos** ventana en un formulario Windows Forms.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para agregar controles enlazados a las clases de entidad  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Desde el **orígenes de datos** ventana, arrastre la **cliente** nodo hasta Form1.  
  
    > [!NOTE]
    >  Para mostrar la **orígenes de datos** ventana, haga clic en **Mostrar orígenes de datos** en el **datos** menú.  
  
3.  Abra Form1 en el Editor de código.  
  
4.  Agregue al formulario el código siguiente, global para el formulario, fuera de cualquier método concreto, pero dentro de la clase Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  Cree un controlador de eventos para el evento `Form_Load` y agregue el código siguiente al controlador:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>Implementar la funcionalidad de guardar  
 De forma predeterminada, el botón Guardar no está habilitado y la funcionalidad de guardar no está implementada. Además, no se agrega automáticamente código para guardar los datos modificados en la base de datos cuando se crean controles enlazados a datos para los orígenes de datos de objeto. En esta sección se explica cómo habilitar el botón Guardar e implementar la funcionalidad de guardar para los objetos de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### <a name="to-implement-save-functionality"></a>Para implementar la funcionalidad de guardar  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Seleccione la operación de guardar situado en la **CustomerBindingNavigator** (el botón con el icono de disquete).  
  
3.  En el **propiedades** ventana, establezca el **habilitado** propiedad **True**.  
  
4.  Haga doble clic en el botón Guardar para crear un controlador de eventos y cambiar al Editor de código.  
  
5.  Agregue el código siguiente al controlador de eventos del botón Guardar:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Invalidar el comportamiento predeterminado para realizar actualizaciones (inserciones, actualizaciones y eliminaciones)  
  
#### <a name="to-override-the-default-update-behavior"></a>Para invalidar el comportamiento de actualización predeterminado  
  
1.  Abra el archivo de LINQ to SQL en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Haga doble clic en el **Northwind.dbml** en el archivo **el Explorador de soluciones**.)  
  
2.  En **Explorador de servidores**/**el Explorador de base de datos**, expanda las bases de datos de Northwind **procedimientos almacenados** nodo y busque el  **InsertCustomers**, **UpdateCustomers**, y **DeleteCustomers** procedimientos almacenados.  
  
3.  Arrastre los tres procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione el **cliente** clase de entidad en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  En el **propiedades** ventana, seleccione la **insertar** propiedad.  
  
6.  Haga clic en el botón de puntos suspensivos (...) junto a **en tiempo de ejecución de uso** para abrir el **configurar comportamiento** cuadro de diálogo.  
  
7.  Seleccione **personalizar**.  
  
8.  Seleccione el **InsertCustomers** método en el **personalizar** lista.  
  
9. Haga clic en **aplicar** para guardar la configuración de la clase y comportamiento seleccionados.  
  
    > [!NOTE]
    >  Puede seguir configurar el comportamiento para cada combinación de clase y comportamiento mientras hace clic en **aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic en **aplicar**, un cuadro de diálogo de advertencia que aparecerá una oportunidad para aplicar los cambios.  
  
10. Seleccione **actualización** en el **comportamiento** lista.  
  
11. Seleccione **personalizar**.  
  
12. Seleccione el **UpdateCustomers** método en el **personalizar** lista.  
  
     Examine la lista de **argumentos de método** y **propiedades de la clase** y observe que hay dos **argumentos de método** y dos **propiedades de la clase**para algunas columnas de la tabla. De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.  
  
13. Mapa de la **Original_CustomerID** argumento de método para el **CustomerID (Original)** propiedad de clase.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan. Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el Object Relational Designer no puede determinar la asignación correcta. Además, si los argumentos de método no tienen propiedades de clase válida para asignar a, puede establecer la **propiedades de la clase** valor **(ninguno)**.  
  
14. Haga clic en **aplicar** para guardar la configuración de la clase y comportamiento seleccionados.  
  
15. Seleccione **eliminar** en el **comportamiento** lista.  
  
16. Seleccione **personalizar**.  
  
17. Seleccione el **DeleteCustomers** método en el **personalizar** lista.  
  
18. Mapa de la **Original_CustomerID** argumento de método para el **CustomerID (Original)** propiedad de clase.  
  
19. Haga clic en **Aceptar**.  
  
> [!NOTE]
>  Aunque no es un asunto de este tutorial particular, vale la pena observar que [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] procesa los valores generados por la base de datos automáticamente para las columnas identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y columnas de marca de tiempo durante las inserciones y actualizaciones. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ejecute la aplicación para comprobar que la **UpdateCustomers** procedimiento almacenado actualiza correctamente el registro de cliente en la base de datos.  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1.  Presione F5.  
  
2.  Modifique un registro en la cuadrícula para probar el comportamiento de actualización.  
  
3.  Agregue un nuevo registro para probar el comportamiento de inserción.  
  
4.  Haga clic en el botón Guardar para volver a guardar los cambios en la base de datos.  
  
5.  Cierre el formulario.  
  
6.  Presione F5 y compruebe que se conservan el registro actualizado y el registro que se acaba de insertar.  
  
7.  Elimine el nuevo registro creado en el paso 3 para probar el comportamiento de eliminación.  
  
8.  Haga clic en el botón Guardar para enviar los cambios y quitar el registro eliminado de la base de datos  
  
9. Cierre el formulario.  
  
10. Presione F5 y compruebe que el registro eliminado se quitó de la base de datos.  
  
    > [!NOTE]
    >  Si su aplicación utiliza SQL Server Express Edition, dependiendo del valor de la **copiar en el directorio de salida** propiedad del archivo de base de datos, los cambios no pueden aparecer al presionar F5 en el paso 10. 
  
## <a name="next-steps"></a>Pasos siguientes  
Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden dar después de crear las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Entre las mejoras que podría realizar a esta aplicación se incluyen:  
  
-   Implementar la comprobación de simultaneidad durante las actualizaciones. Para obtener información, consulte [simultaneidad optimista: información general sobre](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).  
  
-   Agregar consultas LINQ para filtrar los datos. Para obtener información, consulte [Introducción a las consultas de LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="see-also"></a>Vea también
[LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[Métodos de DataContext](../data-tools/datacontext-methods-o-r-designer.md)   
[Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[Consultas LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 