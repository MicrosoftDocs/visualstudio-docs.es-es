---
title: "Tutorial: Crear procedimientos almacenados de actualizaci&#243;n para la tabla Customers de Northwind | Microsoft Docs"
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
  - "Northwind (base de datos de ejemplo)"
  - "Diseñador relacional de objetos, procedimientos almacenados"
  - "procedimientos almacenados [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Tutorial: Crear procedimientos almacenados de actualizaci&#243;n para la tabla Customers de Northwind
Algunos temas de Ayuda en la documentación de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] requieren procedimientos almacenados adicionales en la base de datos de ejemplo Northwind para realizar actualizaciones \(inserciones, actualizaciones y eliminaciones\) de los datos en la tabla Customers.  
  
 Este tutorial ofrece instrucciones para crear estos procedimientos almacenados adicionales en la base de datos de ejemplo Northwind para [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 La sección Pasos siguientes, más adelante en este tema, incluye vínculos a temas que muestran cómo trabajar con estos procedimientos almacenados adicionales.  
  
 Durante este tutorial, aprenderá a realizar las siguientes tareas:  
  
-   Crear una conexión de datos a la base de datos de ejemplo Northwind.  
  
-   Crear los procedimientos almacenados.  
  
## Requisitos previos  
 Para completar este tutorial, necesita lo siguiente:  
  
-   Acceso a la versión de SQL Server de la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Conectar con la base de datos Northwind  
 Este tutorial requiere una conexión a la versión de SQL Server de la base de datos Northwind.  El procedimiento siguiente proporciona instrucciones para crear la conexión de datos.  
  
> [!NOTE]
>  Si ya tiene una conexión de datos a la base de datos Northwind, puede ir a la sección siguiente, Crear los procedimientos almacenados.  
  
#### Para crear una conexión de datos a versión de SQL Server de la base de datos Northwind  
  
1.  En el menú **Ver**, haga clic en **Explorador de servidores**\/**Explorador de bases de datos**.  
  
2.  Haga clic con el botón secundario en **Conexiones de datos** y haga clic en **Agregar conexión**.  
  
3.  En el cuadro de diálogo **Elegir origen de datos**, haga clic en **Microsoft SQL Server** y en **Aceptar**.  
  
     Si se abre el cuadro de diálogo **Agregar conexión** y el **Origen de datos** no es **Microsoft SQL Server \(SqlClient\)**, haga clic en **Cambiar** para abrir el cuadro de diálogo **Elegir\/Cambiar origen de datos**, haga clic en **Microsoft SQL Server** y en **Aceptar**.  
  
4.  En la lista desplegable **Nombre del servidor** haga clic o escriba el nombre del servidor en el que se encuentra la base de datos Northwind.  
  
5.  Dependiendo de los requisitos de la base de datos o de la aplicación, haga clic en **Utilizar autenticación de Windows** o use un nombre de usuario y una contraseña específicos para iniciar sesión en el equipo en que se ejecuta SQL Server \(**Autenticación de SQL Server**\).  
  
6.  En la lista **Seleccionar o escribir nombre de base de datos**, haga clic en la base de datos Northwind.  
  
7.  Haga clic en **Aceptar**.  
  
     La conexión de datos se agrega al **Explorador de servidores**\/**Explorador de bases de datos**.  
  
## Crear los procedimientos almacenados  
 Para crear los procedimientos almacenados, ejecute el script de SQL proporcionado en la base de datos Northwind usando las [Visual Database Tools](http://msdn.microsoft.com/es-es/6b145922-2f00-47db-befc-bf351b4809a1) disponibles en el **Explorador de servidores**\/**Explorador de bases de datos**.  
  
#### Para crear los procedimientos almacenados usando un script de SQL  
  
1.  Expanda la base de datos Northwind en el **Explorador de servidores**\/**Explorador de bases de datos**.  
  
2.  Haga clic con el botón secundario en el nodo **Procedimientos almacenados** y haga clic en **Agregar nuevo procedimiento almacenado**.  
  
3.  Pegue el código siguiente en el Editor de código, reemplazando la plantilla `CREATE PROCEDURE`:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Seleccione todo el texto en el Editor de código, haga clic con el botó secundario en el texto seleccionado y haga clic en **Ejecutar selección**.  
  
     Se crean los procedimientos almacenados SelectCustomers, InsertCustomers, UpdateCustomers y DeleteCustomers para la base de datos Northwind.  
  
## Pasos siguientes  
 Ahora que ha creado los procedimientos almacenados, pruebe los tutoriales siguientes que muestran cómo trabajar con ellos:  
  
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)