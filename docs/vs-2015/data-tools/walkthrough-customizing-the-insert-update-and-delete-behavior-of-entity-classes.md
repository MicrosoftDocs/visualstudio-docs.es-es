---
title: 'Tutorial: Personalización de la inserción, actualización y eliminación de comportamiento de las clases de entidad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 307722b668a71dd97e6b05364226d8c5ea62af66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988786"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Tutorial: Personalización del comportamiento de inserción, actualización y eliminación de clases de entidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona una superficie de diseño visual para crear y editar [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] clases (clases de entidad) que se basan en los objetos de una base de datos. Mediante el uso de [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), puede usar la tecnología LINQ para las bases de datos SQL de acceso. Para más información, consulte [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 El motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] proporciona, de forma predeterminada, la lógica para realizar actualizaciones. El motor en tiempo de ejecución crea las instrucciones predeterminadas de inserción, actualización y eliminación basándose en el esquema de la tabla (definiciones de columna e información de la clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados. Para obtener más información, consulte [personalizar operaciones utilizando procedimientos almacenados](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
> Este tutorial requiere la disponibilidad de los procedimientos almacenados **InsertCustomer**, **UpdateCustomer** y **DeleteCustomer** para la base de datos Northwind.
  
 En este tutorial se proporcionan los pasos que se deben seguir para invalidar el comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL y volver a guardar los datos en una base de datos mediante procedimientos almacenados.  
  
 Durante este tutorial, aprenderá a realizar las siguientes tareas:  
  
-   Crear una nueva aplicación de Windows Forms y agregarle un archivo de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
-   Crear una clase de entidad asignada a la tabla Customers de Northwind.  
  
-   Crear un origen de datos de objeto que haga referencia a la clase Customer de LINQ to SQL.  
  
-   Crear un formulario Windows Forms con un control <xref:System.Windows.Forms.DataGridView> enlazado a la clase Customer.  
  
-   Implementar la funcionalidad de guardar para el formulario.  
  
-   Crear los métodos de <xref:System.Data.Linq.DataContext> agregando procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
-   Configurar la clase Customer de modo que se usen los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este tutorial, necesita lo siguiente:  
  
-   Acceso a la versión de SQL Server de la base de datos de ejemplo Northwind.
  
-   El **InsertCustomer**, **UpdateCustomer**, y **DeleteCustomer** procedimientos almacenados para la base de datos Northwind.
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Crear una aplicación y agregar clases de LINQ to SQL  
 Dado que va a trabajar con clases de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] y mostrar los datos en un Windows Form, cree una nueva aplicación de Windows Forms y agregue un archivo de clases de LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Para crear un nuevo proyecto de aplicación para Windows con clases de LINQ to SQL  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Denomine el proyecto **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    >  Se admite el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] en los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y de C#. Por consiguiente, cree el nuevo proyecto en uno de estos lenguajes.  
  
3.  Haga clic en el **aplicación de Windows Forms** plantilla y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Se crea el proyecto UpdatingwithSProcsWalkthrough y se agrega a **el Explorador de soluciones**.  
  
4.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
5.  Haga clic en la plantilla **Clases de LINQ to SQL** y escriba **Northwind.dbml** en el cuadro **Nombre**.  
  
6.  Haga clic en **Agregar**.  
  
     Se agrega al proyecto un archivo de clases de LINQ to SQL vacío (Northwind.dbml) y se abre el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Crear la clase de entidad Customer y el origen de datos de objeto  
 Crear [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] clases que se asignan a las tablas de base de datos arrastrando las tablas del **Explorador de servidores**/**Database Explorer** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos. Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para crear una clase de entidad Customer y configurar con ella un origen de datos  
  
1.  En **Explorador de servidores**/**Database Explorer**, busque la tabla Customer en la versión de SQL Server de la base de datos de ejemplo Northwind.
  
2.  Arrastre el **clientes** nodo desde **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] superficie.  
  
     Se crea una clase de entidad denominada **Customer**. Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers. La clase de entidad se denomina **Customer** (no **Customers**) porque representa a un único cliente de la tabla Customers.  
  
    > [!NOTE]
    >  Este comportamiento de cambio de nombre se denomina *pluralización*. Se puede activar o desactivar el [cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md). Para obtener más información, vea [Cómo: Activación y desactivación de la pluralización (Object Relational Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  En el menú **Compilar**, haga clic en **Generar UpdatingwithSProcsWalkthrough** para crear el proyecto.  
  
4.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
5.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
6.  Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.  
  
7.  Expanda el nodo **UpdatingwithSProcsWalkthrough** y, después, busque y seleccione la clase **Customer**.  
  
    > [!NOTE]
    >  Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
  
8.  Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Crear un control DataGridView para mostrar los datos del cliente en un formulario Windows Forms  
 Crear controles enlazados a las clases de entidad arrastrando [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] elementos de origen de datos la **orígenes de datos** ventana en un formulario de Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para agregar controles enlazados a las clases de entidad  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Desde el **orígenes de datos** ventana, arrastre el **cliente** nodo hasta Form1.  
  
    > [!NOTE]
    >  Para mostrar la ventana **Orígenes de datos**, haga clic en **Mostrar orígenes de datos** en el menú **Datos**.  
  
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
 De forma predeterminada, el botón Guardar no está habilitado y la funcionalidad de guardar no está implementada. Además, no se agrega automáticamente código para guardar los datos modificados en la base de datos cuando se crean controles enlazados a datos para los orígenes de datos de objeto. En esta sección se explica cómo habilitar el botón Guardar e implementar la funcionalidad de guardar para los objetos de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-implement-save-functionality"></a>Para implementar la funcionalidad de guardar  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Seleccione el botón Guardar en **CustomersBindingNavigator** (el botón con el icono del disquete).  
  
3.  En la ventana **Propiedades**, establezca la propiedad **Enabled** en **True**.  
  
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
  
1.  Abra el archivo de LINQ to SQL en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Haga doble clic en el archivo **Northwind.dbml** en el **Explorador de soluciones**.  
  
2.  En **Explorador de servidores**/**Database Explorer**, expanda las bases de datos de Northwind **Stored Procedures** nodo y busque el  **InsertCustomers**, **UpdateCustomers**, y **DeleteCustomers** procedimientos almacenados.  
  
3.  Arrastre los tres procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione el **cliente** clase de entidad en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  En la ventana **Propiedades**, seleccione la propiedad **Insertar**.  
  
6.  Haga clic en el botón de puntos suspensivos (...) junto a **en tiempo de ejecución Use** para abrir el **configurar comportamiento** cuadro de diálogo.  
  
7.  Seleccione **Personalizar**.  
  
8.  Seleccione el método **InsertCustomers** en la lista **Personalizar**.  
  
9. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.  
  
    > [!NOTE]
    >  Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic **aplicar**, que proporciona una oportunidad para aplicar cualquier cambio aparecerá un cuadro de diálogo de advertencia.  
  
10. Seleccione **Actualizar** en la lista **Comportamiento**.  
  
11. Seleccione **Personalizar**.  
  
12. Seleccione el método **UpdateCustomers** en la lista **Personalizar**.  
  
     Examine la lista de **Argumentos de método** y **Propiedades de clase**, y observe que hay dos **argumentos de método** y dos **propiedades de clase** para algunas columnas de la tabla. De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.  
  
13. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)**.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan. Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el Object Relational Designer no puede determinar la asignación correcta. Además, si los argumentos de método no tienen propiedades de clase válidas a las que asignarse, puede establecer el valor de **Propiedades de clase** en **(Ninguno)**.  
  
14. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.  
  
15. Seleccione **Eliminar** en la lista **Comportamiento**.  
  
16. Seleccione **Personalizar**.  
  
17. Seleccione el método **DeleteCustomers** en la lista **Personalizar**.  
  
18. Asigne el argumento de método **Original_CustomerID** a la propiedad de clase **CustomerID (Original)**.  
  
19. Haga clic en **Aceptar**.  
  
> [!NOTE]
>  Aunque no es un asunto de este tutorial particular, vale la pena observar que [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] procesa los valores generados por la base de datos automáticamente para las columnas identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y columnas de marca de tiempo durante las inserciones y actualizaciones. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Vuelva a ejecutar la aplicación para comprobar que el procedimiento almacenado **UpdateCustomers** actualiza correctamente el registro de cliente en la base de datos.  
  
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
    > Si la aplicación usa SQL Server Express Edition, dependiendo del valor de la **Copy to Output Directory** propiedad del archivo de base de datos, los cambios no es posible que aparezcan al presionar F5 en el paso 10.
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden dar después de crear las clases de entidad de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Entre las mejoras que podría realizar a esta aplicación se incluyen:  
  
-   Implementar la comprobación de simultaneidad durante las actualizaciones. Para obtener información, consulte [simultaneidad optimista: Información general sobre](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Agregar consultas LINQ para filtrar los datos. Para obtener información, consulte [Introducción a las consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Consultas LINQ to SQL](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE cuáles son las novedades para el desarrollo de aplicaciones de datos en Visual Studio 2012](http://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
