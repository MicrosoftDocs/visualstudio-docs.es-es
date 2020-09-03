---
title: Crear una base de datos SQL mediante un script | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670092"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Creación de una base de datos SQL mediante un script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, se usa Visual Studio para crear una base de datos pequeña que contiene el código de ejemplo para [crear una aplicación de datos sencilla mediante ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **En este tema**

- [Crear un script que contiene un esquema de la base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Crear un proyecto de base de datos e importar un esquema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Implementar la base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Prerrequisitos
 Para completar este tutorial, debe tener instalado SQL Server Express LocalDB u otra base de datos SQL.

## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a> Crear un script que contiene un esquema de base de datos

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Para crear un script desde el que se puede importar un esquema

1. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , en la barra de menús, seleccione **archivo**  >  **nuevo**  >  **archivo**.

     Aparece el cuadro de diálogo **Nuevo archivo** .

2. En la lista de **categorías** , seleccione **General**.

3. En la lista de **plantillas** , seleccione **archivo SQL**y, a continuación, seleccione el botón **abrir** .

     Se abre el editor de Transact-SQL.

4. Copie el siguiente código de Transact-SQL y péguelo en el editor de Transact-SQL.

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

5. En la barra de menús, seleccione **archivo**  >  **Guardar SqlQuery_1. SQL como**.

     Aparece el cuadro de diálogo **Guardar archivo como** .

6. En el cuadro **nombre de archivo** , escriba `SampleImportScript.sql` , anote la ubicación donde guardará el archivo y, a continuación, seleccione el botón **Guardar** .

7. En la barra de menús, seleccione **archivo**  >  **cerrar solución**.

     A continuación, cree un proyecto de base de datos y, a continuación, importe el esquema desde el script que ha creado.

## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProject"></a> Crear un proyecto de base de datos e importar un esquema

#### <a name="to-create-a-database-project"></a>Para crear un proyecto de base de datos

1. En la barra de menús, seleccione **Archivo**  > **Nuevo** > **Proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. En **instalado**, expanda el nodo **plantillas** , expanda el nodo **otros lenguajes** , seleccione la categoría **SQL Server** y, a continuación, seleccione la plantilla **proyecto de base de datos SQL Server** .

    > [!NOTE]
    > El nodo **otros lenguajes** no aparece en todas las instalaciones de Visual Studio.

3. En el cuadro **nombre** , escriba `Small Database` .

4. Active la casilla **Crear directorio para la solución** si aún no está seleccionada.

5. Desactive la casilla **Agregar al control de código fuente** si aún no está desactivada y, a continuación, seleccione el botón **Aceptar** .

     Se crea el proyecto de base de datos, que aparece en el **Explorador de soluciones**.

     A continuación, importe el esquema de la base de datos desde el script.

#### <a name="to-import-a-database-schema-from-a-script"></a>Para importar un esquema de la base de datos de un script

1. En la barra de menús, seleccione **proyecto**  >  **importar**  >  **script**.

2. En la página de **bienvenida** , revise el texto y, a continuación, seleccione el botón **siguiente** .

3. Seleccione el botón de opción **archivo único** y, a continuación, seleccione el botón **examinar** .

     Aparecerá el cuadro de diálogo **importar script SQL** .

4. Abra la carpeta donde guardó el archivo SampleImportScript. SQL, seleccione el archivo y, a continuación, seleccione el botón **abrir** .

5. Seleccione el botón **Finalizar** para cerrar el cuadro de diálogo **importar script SQL** .

     Se importa el script y los objetos que define el script se agregan al proyecto de base de datos.

6. Revise el Resumen y, a continuación, haga clic en el botón **Finalizar** para cerrar el cuadro de diálogo **Importar archivo de script SQL** .

7. En **Explorador de soluciones**, expanda las carpetas ventas, scripts y seguridad del proyecto y compruebe que contienen archivos. SQL.

8. En **Explorador de objetos de SQL Server**, compruebe que la base de datos aparece bajo el nodo **proyectos** .

     En este momento, la base de datos solo contiene objetos del sistema, como tablas y procedimientos almacenados. Después de implementar la base de datos, contendrá las tablas de usuario y los procedimientos almacenados definidos por los scripts.

## <a name="deploy-the-database"></a><a name="DeployDatabase"></a> Implementar la base de datos
 Al presionar la tecla **F5** , se implementa (o publica) la base de datos en una base de datos LocalDB de forma predeterminada. Puede implementar la base de datos en una ubicación diferente; para ello, abra la página de propiedades del proyecto, seleccione la pestaña **depurar** y, a continuación, cambie la cadena de conexión.
