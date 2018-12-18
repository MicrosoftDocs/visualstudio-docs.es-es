---
title: 'Tutorial: Personalizar la inserción, actualización y eliminación de comportamiento de las clases de entidad | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d8ef69258d9c672bb5deb01b9c2e0972d4e8303
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193549"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Tutorial: Personalizar la inserción, actualización y eliminación de comportamiento de las clases de entidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona una superficie de diseño visual para crear y editar [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] clases (clases de entidad) que se basan en los objetos de una base de datos. Mediante el uso de [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), puede usar la tecnología LINQ para las bases de datos SQL de acceso. Para más información, consulte [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 El motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] proporciona, de forma predeterminada, la lógica para realizar actualizaciones. El motor en tiempo de ejecución crea las instrucciones predeterminadas de inserción, actualización y eliminación basándose en el esquema de la tabla (definiciones de columna e información de la clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados. Para obtener más información, consulte [personalizar operaciones utilizando procedimientos almacenados](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
>  En este tutorial requiere la disponibilidad de la **InsertCustomer**, **UpdateCustomer**, y **DeleteCustomer** procedimientos almacenados para la base de datos Northwind. Para obtener más información sobre cómo crear estos procedimientos almacenados, vea [Tutorial: crear actualización procedimientos almacenados para la tabla Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
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
  
-   Acceso a la versión de SQL Server de la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
-   El **InsertCustomer**, **UpdateCustomer**, y **DeleteCustomer** procedimientos almacenados para la base de datos Northwind. Para obtener más información, consulte [Tutorial: crear actualización procedimientos almacenados para la tabla Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
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
  
5.  Haga clic en el **clases LINQ to SQL** plantilla y escriba **Northwind.dbml** en el **nombre** cuadro.  
  
6.  Haga clic en **Agregar**.  
  
     Se agrega al proyecto un archivo de clases de LINQ to SQL vacío (Northwind.dbml) y se abre el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Crear la clase de entidad Customer y el origen de datos de objeto  
 Crear [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] clases que se asignan a las tablas de base de datos arrastrando las tablas del **Explorador de servidores**/**Database Explorer** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos. Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Para crear una clase de entidad Customer y configurar con ella un origen de datos  
  
1.  En **Explorador de servidores**/**Database Explorer**, busque la tabla Customer en la versión de SQL Server de la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: conectarse a la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Arrastre el **clientes** nodo desde **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] superficie.  
  
     Una clase de entidad denominada **cliente** se crea. Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers. La clase de entidad se denomina **cliente** (no **clientes**) porque representa un único cliente de la tabla Customers.  
  
    > [!NOTE]
    >  Este comportamiento de cambio de nombre se denomina *pluralización*. Se puede activar o desactivar el [cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md). Para obtener más información, consulte [Cómo: activar y desactivar (Object Relational Designer) la pluralización](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  En el **compilar** menú, haga clic en **generar UpdatingwithSProcsWalkthrough** para compilar el proyecto.  
  
4.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
5.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
6.  Haga clic en **objeto** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.  
  
7.  Expanda el **UpdatingwithSProcsWalkthrough** nodo y busque y seleccione el **cliente** clase.  
  
    > [!NOTE]
    >  Si el **cliente** clase no está disponible, cancele el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
  
8.  Haga clic en **finalizar** para crear el origen de datos y agregar el **cliente** clase de entidad para el **orígenes de datos** ventana.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Crear un control DataGridView para mostrar los datos del cliente en un formulario Windows Forms  
 Crear controles enlazados a las clases de entidad arrastrando [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] elementos de origen de datos la **orígenes de datos** ventana en un formulario de Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Para agregar controles enlazados a las clases de entidad  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Desde el **orígenes de datos** ventana, arrastre el **cliente** nodo hasta Form1.  
  
    > [!NOTE]
    >  Para mostrar el **orígenes de datos** ventana, haga clic en **Mostrar orígenes de datos** en el **datos** menú.  
  
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
  
2.  Seleccione Guardar situado en la **CustomerBindingNavigator** (el botón con el icono del disquete).  
  
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
  
1.  Abra el archivo de LINQ to SQL en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Haga doble clic en el **Northwind.dbml** archivo **el Explorador de soluciones**.)  
  
2.  En **Explorador de servidores**/**Database Explorer**, expanda las bases de datos de Northwind **Stored Procedures** nodo y busque el  **InsertCustomers**, **UpdateCustomers**, y **DeleteCustomers** procedimientos almacenados.  
  
3.  Arrastre los tres procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione el **cliente** clase de entidad en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  En el **propiedades** ventana, seleccione el **insertar** propiedad.  
  
6.  Haga clic en el botón de puntos suspensivos (...) junto a **en tiempo de ejecución Use** para abrir el **configurar comportamiento** cuadro de diálogo.  
  
7.  Seleccione **personalizar**.  
  
8.  Seleccione el **InsertCustomers** método en el **personalizar** lista.  
  
9. Haga clic en **aplicar** para guardar la configuración de la clase seleccionada y el comportamiento.  
  
    > [!NOTE]
    >  Puede seguir configurar el comportamiento para cada combinación de clase y comportamiento, siempre haga clic en **aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic **aplicar**, que proporciona una oportunidad para aplicar cualquier cambio aparecerá un cuadro de diálogo de advertencia.  
  
10. Seleccione **actualización** en el **comportamiento** lista.  
  
11. Seleccione **personalizar**.  
  
12. Seleccione el **UpdateCustomers** método en el **personalizar** lista.  
  
     Examine la lista de **argumentos de método** y **propiedades de la clase** y tenga en cuenta que hay dos **argumentos de método** y dos **propiedades de la clase**para algunas columnas de la tabla. De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.  
  
13. Mapa del **Original_CustomerID** argumento de método para el **CustomerID (Original)** propiedad de clase.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan. Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el Object Relational Designer no puede determinar la asignación correcta. Además, si los argumentos de método no tienen propiedades de clase válido para asignar a, puede establecer el **propiedades de la clase** valor **(ninguno)**.  
  
14. Haga clic en **aplicar** para guardar la configuración de la clase seleccionada y el comportamiento.  
  
15. Seleccione **eliminar** en el **comportamiento** lista.  
  
16. Seleccione **personalizar**.  
  
17. Seleccione el **DeleteCustomers** método en el **personalizar** lista.  
  
18. Mapa del **Original_CustomerID** argumento de método para el **CustomerID (Original)** propiedad de clase.  
  
19. Haga clic en **Aceptar**.  
  
> [!NOTE]
>  Aunque no es un asunto de este tutorial particular, vale la pena observar que [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] procesa los valores generados por la base de datos automáticamente para las columnas identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y columnas de marca de tiempo durante las inserciones y actualizaciones. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.  
  
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
    >  Si la aplicación usa SQL Server Express Edition, dependiendo del valor de la **Copy to Output Directory** propiedad del archivo de base de datos, los cambios no es posible que aparezcan al presionar F5 en el paso 10. Para obtener más información, consulte [Cómo: administrar archivos de datos locales en el proyecto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden dar después de crear las clases de entidad de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Entre las mejoras que podría realizar a esta aplicación se incluyen:  
  
-   Implementar la comprobación de simultaneidad durante las actualizaciones. Para obtener información, consulte [simultaneidad optimista: información general sobre](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Agregar consultas LINQ para filtrar los datos. Para obtener información, consulte [Introducción a las consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Consultas LINQ to SQL](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE cuáles son las novedades para el desarrollo de aplicaciones de datos en Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

