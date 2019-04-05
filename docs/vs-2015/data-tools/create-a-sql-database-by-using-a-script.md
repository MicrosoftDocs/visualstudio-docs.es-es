---
title: Crear una base de datos SQL mediante una secuencia de comandos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dc35def483b80610b9480dfd57320712d75fe0eb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995504"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Crear una base de datos SQL mediante una secuencia de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En este tutorial, use Visual Studio para crear una base de datos pequeño que contiene el código de ejemplo para [crear una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **En este tema**  
  
-   [Crear un script que contiene un esquema de base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Crear un proyecto de base de datos e importar un esquema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Implementar la base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe tener SQL Server Express LocalDB o en otra base de datos SQL, instalado.  
  
##  <a name="CreateScript"></a> Crear un script que contiene un esquema de base de datos  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Para crear un script desde el que puede importar un esquema  
  
1.  En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en la barra de menús, seleccione **archivo** > **New** > **archivo**.  
  
     El **nuevo archivo** aparece el cuadro de diálogo.  
  
2.  En el **categorías** lista, seleccione **General**.  
  
3.  En el **plantillas** lista, seleccione **archivo Sql**y, a continuación, seleccione el **abierto** botón.  
  
     Se abrirá el editor de Transact-SQL.  
  
4.  Copie el siguiente código Transact-SQL y, a continuación, péguelo en el editor de Transact-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  En la barra de menús, seleccione **archivo** > **Guardar SqlQuery_1.sql como**.  
  
     El **Guardar archivo como** aparece el cuadro de diálogo.  
  
6.  En el **nombre de archivo** , escriba `SampleImportScript.sql`, tenga en cuenta la ubicación donde podrá guardar el archivo y, a continuación, seleccione el **guardar** botón.  
  
7.  En la barra de menús, seleccione **Archivo** > **Cerrar solución**.  
  
     A continuación, cree un proyecto de base de datos y, a continuación, importar el esquema de la secuencia de comandos que ha creado.  
  
##  <a name="CreateProject"></a> Crear un proyecto de base de datos e importar un esquema  
  
#### <a name="to-create-a-database-project"></a>Para crear un proyecto de base de datos  
  
1.  En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En **instalado**, expanda el **plantillas** nodo, expanda el **otros lenguajes** nodo, seleccione el **SQL Server** categoría y, a continuación, Seleccione el **el proyecto de base de datos de SQL Server** plantilla.  
  
    > [!NOTE]
    >  El **otros lenguajes** nodo no aparece en todas las instalaciones de Visual Studio.  
  
3.  En el **nombre** , escriba `Small Database`.  
  
4.  Seleccione el **crear directorio para la solución** casilla de verificación si aún no está seleccionado.  
  
5.  Desactive el **agregar al control de código fuente** casilla de verificación si aún no está desactivada y, a continuación, seleccione el **Aceptar** botón.  
  
     El proyecto de base de datos se crea y aparece en **el Explorador de soluciones**.  
  
     A continuación, importe el esquema de base de datos de la secuencia de comandos.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Para importar un esquema de base de datos de una secuencia de comandos  
  
1.  En la barra de menús, seleccione **proyecto** > **importación** > **Script**.  
  
2.  En el **bienvenida** , revise el texto y, a continuación, seleccione el **siguiente** botón.  
  
3.  Seleccione el **único archivo** botón de opción y, a continuación, seleccione el **examinar** botón.  
  
     El **importar SQL Script** aparece el cuadro de diálogo.  
  
4.  Abra la carpeta donde guardó el archivo SampleImportScript.sql, seleccione el archivo y, a continuación, seleccione el **abierto** botón.  
  
5.  Seleccione el **finalizar** botón para cerrar el **importar SQL Script** cuadro de diálogo.  
  
     Se importa el script y los objetos que define la secuencia de comandos se agregan a su proyecto de base de datos.  
  
6.  Revise el resumen y, a continuación, haga clic en el **finalizar** botón para cerrar el **importar archivo de Script SQL** cuadro de diálogo.  
  
7.  En **el Explorador de soluciones**, expanda ventas, Scripts y seguridad de las carpetas del proyecto y compruebe que contienen los archivos .sql.  
  
8.  En **Explorador de objetos de SQL Server**, compruebe que la base de datos aparece bajo el **proyectos** nodo.  
  
     En este momento, la base de datos contiene solo los objetos del sistema, como tablas y procedimientos almacenados. Después de implementar la base de datos, contendrá las tablas de usuario y procedimientos almacenados que definen las secuencias de comandos.  
  
##  <a name="DeployDatabase"></a> Implementar la base de datos  
 Cuando presiona el **F5** clave, implementar (o publicar) la base de datos a una base de datos LocalDB de forma predeterminada. Puede implementar la base de datos a una ubicación diferente, abra la página de propiedades para el proyecto, seleccionando la **depurar** ficha y, a continuación, cambiar la cadena de conexión.
