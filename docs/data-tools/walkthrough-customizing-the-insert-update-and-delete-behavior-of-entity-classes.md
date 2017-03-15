---
title: "Tutorial: Personalizar el comportamiento de inserci&#243;n, actualizaci&#243;n y eliminaci&#243;n de las clases de entidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Personalizar el comportamiento de inserci&#243;n, actualizaci&#243;n y eliminaci&#243;n de las clases de entidad
El [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona una superficie de diseño visual para crear y editar las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(clases de entidad\) basadas en los objetos de una base de datos.Mediante [LINQ a SQL](../Topic/LINQ%20to%20SQL.md), puede usar la tecnología LINQ para obtener acceso a las bases de datos SQL.Para obtener más información, consulte [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 El motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] proporciona, de forma predeterminada, la lógica para realizar actualizaciones.El motor en tiempo de ejecución crea las instrucciones predeterminadas de inserción, actualización y eliminación basándose en el esquema de la tabla \(definiciones de columna e información de la clave principal\).Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización y designar procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder trabajar con los datos de la base de datos.También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas.Además, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.Para obtener más información, vea [Personalizar las operaciones mediante procedimientos almacenados exclusivamente](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md).  
  
> [!NOTE]
>  Este tutorial requiere la disponibilidad de los procedimientos almacenados **InsertCustomer**, **UpdateCustomer** y **DeleteCustomer** para la base de datos Northwind.Para obtener información detallada sobre cómo crear estos procedimientos almacenados, vea [Tutorial: Crear procedimientos almacenados de actualización para la tabla Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 En este tutorial se proporcionan los pasos que se deben seguir para invalidar el comportamiento predeterminado del motor en tiempo de ejecución LINQ to SQL y volver a guardar los datos en una base de datos mediante procedimientos almacenados.  
  
 En este tutorial, aprenderá a realizar las siguientes tareas:  
  
-   Crear una nueva aplicación de Windows Forms y agregarle un archivo de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
-   Crear una clase de entidad asignada a la tabla Customers de Northwind.  
  
-   Crear un origen de datos de objeto que haga referencia a la clase Customer de LINQ to SQL.  
  
-   Crear un formulario Windows Forms con un control <xref:System.Windows.Forms.DataGridView> enlazado a la clase Customer.  
  
-   Implementar la funcionalidad de guardar para el formulario.  
  
-   Crear los métodos de <xref:System.Data.Linq.DataContext> agregando procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configurar la clase Customer de modo que se usen los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones.  
  
## Requisitos previos  
 Para realizar este tutorial, necesita lo siguiente:  
  
-   Tener acceso a la versión de SQL Server de la base de datos de ejemplo Northwind.Para obtener más información, consulte [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
-   Los procedimientos almacenados **InsertCustomer**, **UpdateCustomer** y **DeleteCustomer** para la base de datos Northwind.Para obtener más información, consulte [Tutorial: Crear procedimientos almacenados de actualización para la tabla Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## Crear una aplicación y agregar clases de LINQ to SQL  
 Dado que va a trabajar con clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] y mostrar los datos en un Windows Form, cree una nueva aplicación de Windows Forms y agregue un archivo de clases de LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear un nuevo proyecto de aplicación para Windows con clases de LINQ to SQL  
  
1.  Desde el menú **Archivo**, cree un proyecto nuevo.  
  
2.  Asigne al proyecto el nombre UpdatingwithSProcsWalkthrough.  
  
    > [!NOTE]
    >  Se admite el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] en los proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y de C\#.Por consiguiente, cree el nuevo proyecto en uno de estos lenguajes.  
  
3.  Haga clic en la plantilla **Aplicación de Windows Forms** y en **Aceptar**.Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto UpdatingwithSProcsWalkthrough y se agrega al **Explorador de soluciones**.  
  
4.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
5.  Haga clic en la plantilla **Clases de LINQ to SQL** y escriba Northwind.dbml en el cuadro **Nombre**.  
  
6.  Haga clic en **Agregar**.  
  
     Se agrega al proyecto un archivo de clases de LINQ to SQL vacío \(Northwind.dbml\) y se abre el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Crear la clase de entidad Customer y el origen de datos de objeto  
 Cree las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que están asignadas a las tablas de base de datos arrastrando las tablas del **Explorador de servidores**\/**Explorador de bases de datos** al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].El resultado serán las clases de entidad de LINQ to SQL que se asignan a las tablas en la base de datos.Después de crear las clases de entidad, éstas se pueden usar como orígenes de datos de objeto igual que cualquier otra clase que tenga propiedades públicas.  
  
#### Para crear una clase de entidad Customer y configurar con ella un origen de datos  
  
1.  En el **Explorador de servidores**\/**Explorador de bases de datos**, busque la tabla Customer en la versión de SQL Server de la base de datos de ejemplo Northwind.Para obtener más información, vea [Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Arrastre el nodo **Customers** del **Explorador de servidores**\/**Explorador de bases de datos** hasta la superficie del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Se crea una clase de entidad denominada **Customer**.Dicha clase tiene propiedades que corresponden a las columnas de la tabla Customers.La clase de entidad se denomina **Customer** \(no **Customers**\) porque representa a un único cliente de la tabla Customers.  
  
    > [!NOTE]
    >  Este comportamiento de cambio de nombre se denomina *pluralización*.Se puede activar o desactivar en [Opciones \(Cuadro de diálogo\)](../ide/reference/options-dialog-box-visual-studio.md).Para obtener más información, vea [Cómo: Activar y desactivar la pluralización \(Object Relational Designer\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  En el menú **Compilar**, haga clic en **Generar UpdatingwithSProcsWalkthrough** para crear el proyecto.  
  
4.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
5.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos**.  
  
6.  Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y, a continuación, haga clic en **Siguiente**.  
  
7.  Expanda el nodo **UpdatingwithSProcsWalkthrough** y, a continuación, busque y seleccione la clase **Customer**.  
  
    > [!NOTE]
    >  Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
  
8.  Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.  
  
## Crear un control DataGridView para mostrar los datos del cliente en un formulario Windows Forms  
 Cree los controles enlazados a las clases de entidad arrastrando los elementos de origen de datos de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] desde la ventana **Orígenes de datos** hasta un formulario Windows Forms.  
  
#### Para agregar controles enlazados a las clases de entidad  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Desde la ventana **Orígenes de datos**, arrastre el nodo **Customer** hasta Form1.  
  
    > [!NOTE]
    >  Para mostrar la ventana **Orígenes de datos**, haga clic en **Mostrar orígenes de datos** en el menú **Datos**.  
  
3.  Abra Form1 en el Editor de código.  
  
4.  Agregue al formulario el código siguiente, global para el formulario, fuera de cualquier método concreto, pero dentro de la clase Form1:  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Cree un controlador de eventos para el evento `Form_Load` y agregue el código siguiente al controlador:  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## Implementar la funcionalidad de guardar  
 De forma predeterminada, el botón Guardar no está habilitado y la funcionalidad de guardar no está implementada.Además, no se agrega automáticamente código para guardar los datos modificados en la base de datos cuando se crean controles enlazados a datos para los orígenes de datos de objeto.En esta sección se explica cómo habilitar el botón Guardar e implementar la funcionalidad de guardar para los objetos de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### Para implementar la funcionalidad de guardar  
  
1.  Abra Form1 en la vista Diseño.  
  
2.  Seleccione el botón Guardar en **CustomersBindingNavigator** \(el botón con el icono del disquete\).  
  
3.  En la ventana **Propiedades**, establezca la propiedad **Enabled** en **True**.  
  
4.  Haga doble clic en el botón Guardar para crear un controlador de eventos y cambiar al Editor de código.  
  
5.  Agregue el código siguiente al controlador de eventos del botón Guardar.  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## Invalidar el comportamiento predeterminado para realizar actualizaciones \(inserciones, actualizaciones y eliminaciones\)  
  
#### Para invalidar el comportamiento de actualización predeterminado  
  
1.  Abra el archivo de LINQ to SQL en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(Haga doble clic en el archivo **Northwind.dbml** en el **Explorador de soluciones**.\)  
  
2.  En el **Explorador de servidores**\/**Explorador de bases de datos**, expanda el nodo **Procedimientos almacenados** de las bases de datos Northwind y busque los procedimientos almacenados **InsertCustomers**, **UpdateCustomers** y **DeleteCustomers**.  
  
3.  Arrastre los tres procedimientos almacenados al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Los procedimientos almacenados se agregan al panel de métodos como métodos de <xref:System.Data.Linq.DataContext>.Para obtener más información, vea [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione la clase de entidad **Customer** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  En la ventana **Propiedades**, seleccione la propiedad **Insertar**.  
  
6.  Haga clic en los puntos suspensivos \(...\) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.  
  
7.  Seleccione **Personalizar**.  
  
8.  Seleccione el método **InsertCustomers** en la lista **Personalizar**.  
  
9. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.  
  
    > [!NOTE]
    >  Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación.Si cambia la clase o el comportamiento antes de hacer clic en **Aplicar**, aparecerá un cuadro de diálogo de advertencia en el que podrá aplicar los cambios.  
  
10. Seleccione **Actualizar** en la lista **Comportamiento**.  
  
11. Seleccione **Personalizar**.  
  
12. Seleccione el método **UpdateCustomers** en la lista **Personalizar**.  
  
     Examine la lista de **Argumentos de método** y **Propiedades de clase**, y observe que hay dos **argumentos de método** y dos **propiedades de clase** para algunas columnas de la tabla.De esta manera, resulta más fácil realizar un seguimiento de los cambios y crear instrucciones que comprueben las infracciones de simultaneidad.  
  
13. Asigne el argumento de método **Original\_CustomerID** a la propiedad de clase **CustomerID \(Original\)**.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignarán a las propiedades de clase cuando los nombres coincidan.Si se modifican los nombres de propiedad y ya no hay coincidencia entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el Object Relational Designer no puede determinar la asignación correcta.Además, si los argumentos de método no tienen propiedades de clase válidas a las que asignarse, puede establecer el valor de **Propiedades de clase** en **\(Ninguno\)**.  
  
14. Haga clic en **Aplicar** para guardar la configuración de la clase y el comportamiento seleccionados.  
  
15. Seleccione **Eliminar** en la lista **Comportamiento**.  
  
16. Seleccione **Personalizar**.  
  
17. Seleccione el método **DeleteCustomers** en la lista **Personalizar**.  
  
18. Asigne el argumento de método **Original\_CustomerID** a la propiedad de clase **CustomerID \(Original\)**.  
  
19. Haga clic en **Aceptar**.  
  
> [!NOTE]
>  Aunque no es un asunto de este tutorial particular, vale la pena observar que [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] procesa los valores generados por la base de datos automáticamente para las columnas identidad \(incremento automático\), rowguidcol \(GUID generado por la base de datos\) y columnas de marca de tiempo durante las inserciones y actualizaciones.Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo.Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Probar la aplicación  
 Vuelva a ejecutar la aplicación para comprobar que el procedimiento almacenado **UpdateCustomers** actualiza correctamente el registro de cliente en la base de datos.  
  
#### Para probar la aplicación  
  
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
    >  Si la aplicación usa SQL Server Express Edition, dependiendo del valor de la propiedad **Copiar en el directorio de resultados** del archivo de base de datos, puede que los cambios no aparezcan al presionar F5 en el paso 10.Para obtener más información, vea [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se pueden dar después de crear las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].A continuación, se indican algunas de las mejoras que podría realizar en esta aplicación:  
  
-   Implementar la comprobación de simultaneidad durante las actualizaciones.Para obtener más información, vea [Simultaneidad optimista: Información general](../Topic/Optimistic%20Concurrency:%20Overview.md).  
  
-   Agregar consultas LINQ para filtrar los datos.Para obtener más información, vea [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Consultas en LINQ to SQL](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/es-es/3d50d68f-5f44-4915-842f-6d42fce793f1)