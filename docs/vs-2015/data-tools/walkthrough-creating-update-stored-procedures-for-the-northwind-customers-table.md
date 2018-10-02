---
title: 'Tutorial: Creación de actualización de procedimientos almacenados para la tabla Customers de Northwind | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: bbcd68b7604f7a80546168406146f326e1bac224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566015"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Tutorial: Crear procedimientos almacenados de actualización para la tabla Customers de Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Algunos temas de ayuda en la [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] documentación requieren procedimientos almacenados adicionales en la base de datos de ejemplo Northwind para realizar actualizaciones (inserciones, actualizaciones y eliminaciones) de datos en la tabla Customers.  
  
 Este tutorial ofrece instrucciones para crear estos procedimientos almacenados adicionales en la base de datos de ejemplo Northwind para [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 La sección Pasos siguientes, más adelante en este tema, incluye vínculos a temas que muestran cómo trabajar con estos procedimientos almacenados adicionales.  
  
 Durante este tutorial, aprenderá a realizar las siguientes tareas:  
  
-   Crear una conexión de datos a la base de datos de ejemplo Northwind.  
  
-   Crear los procedimientos almacenados.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, necesita lo siguiente:  
  
-   Acceso a la versión de SQL Server de la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Conectar con la base de datos Northwind  
 Este tutorial requiere una conexión a la versión de SQL Server de la base de datos Northwind. El procedimiento siguiente proporciona instrucciones para crear la conexión de datos.  
  
> [!NOTE]
>  Si ya tiene una conexión de datos a la base de datos Northwind, puede ir a la sección siguiente, Crear los procedimientos almacenados.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Para crear una conexión de datos a versión de SQL Server de la base de datos Northwind  
  
1.  En el **vista** menú, haga clic en **Explorador de servidores**/**Database Explorer**.  
  
2.  Haga clic en **conexiones de datos** y haga clic en **Agregar conexión**.  
  
3.  En el **Elegir origen de datos** cuadro de diálogo, haga clic en **Microsoft SQL Server**y, a continuación, haga clic en **Aceptar**.  
  
     Si el **Agregar conexión** abre el cuadro de diálogo y el **origen de datos** no **Microsoft SQL Server (SqlClient)**, haga clic en **cambio** para abrir el **Elegir/cambiar origen de datos** cuadro de diálogo, haga clic en **Microsoft SQL Server**y, a continuación, haga clic en **Aceptar**.  
  
4.  Haga clic en un **nombre del servidor** en la lista desplegable, lista o escriba el nombre del servidor en el que se encuentra la base de datos Northwind.  
  
5.  Según los requisitos de la base de datos o la aplicación, haga clic en **utilizar autenticación de Windows** o usar un nombre de usuario específico y una contraseña para iniciar sesión en el equipo que ejecuta SQL Server (**deautenticacióndeSQLServer**).  
  
6.  Haga clic en la base de datos Northwind en el **seleccione o escriba un nombre de base de datos** lista.  
  
7.  Haga clic en **Aceptar**.  
  
     La conexión de datos se agrega a **Explorador de servidores**/**Database Explorer**.  
  
## <a name="creating-the-stored-procedures"></a>Crear los procedimientos almacenados  
 Crear los procedimientos almacenados, ejecute el script SQL proporcionado en la base de datos Northwind utilizando el [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) disponibles en **Explorador de servidores** /  **Explorador de la base de datos**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Para crear los procedimientos almacenados usando un script de SQL  
  
1.  Expanda la base de datos Northwind en **Explorador de servidores**/**Database Explorer**.  
  
2.  Haga clic en el **Stored Procedures** nodo y haga clic en **Agregar nuevo procedimiento almacenado**.  
  
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
  
4.  Seleccione todo el texto en el Editor de código, haga clic en el texto seleccionado y haga clic en **Ejecutar selección**.  
  
     Se crean los procedimientos almacenados SelectCustomers, InsertCustomers, UpdateCustomers y DeleteCustomers para la base de datos Northwind.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora que ha creado los procedimientos almacenados, pruebe los tutoriales siguientes que muestran cómo trabajar con ellos:  
  
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)