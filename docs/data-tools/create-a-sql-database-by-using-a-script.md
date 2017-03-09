---
title: "Tutorial: Crear una peque&#241;a base de datos de ejemplo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Crear una peque&#241;a base de datos de ejemplo
En este tutorial, se usa Visual Studio para crear una pequeña base de datos que contiene el código de ejemplo para [Tutorial: Crear una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **En este tema**  
  
-   [Crear un script que contiene un esquema de base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Crear un proyecto de base de datos e importar un esquema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Implementar la base de datos](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Requisitos previos  
 Para completar este tutorial, debe haber instalado [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  Debe también poder conectarse a un servidor de bases de datos o una base de datos LocalDB donde tenga los permisos necesarios para crear e implementar una base de datos.  
  
##  <a name="CreateScript"></a> Crear un script que contiene un esquema de base de datos  
  
#### Para crear un script del que se puede importar un esquema  
  
1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en la barra de menú, elija **Archivo**, **Nuevo**, **Archivo**.  
  
     Aparece el cuadro de diálogo **Nuevo archivo**.  
  
2.  En la lista **Categorías**, elija **General**.  
  
3.  En la lista de **Plantillas**, elija **Archivo de SQL** y elija el botón **Abrir**.  
  
     Se abre el editor de Transact\-SQL.  
  
4.  Copie el siguiente código de Transact\-SQL y péguelos en el editor de Transact\-SQL.  
  
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
  
5.  En el barra de menú, elija **Archivo**, **Guardar SqlQuery\_1.sql como**.  
  
     Aparece el cuadro de diálogo **Guardar archivo como**.  
  
6.  En el cuadro **Nombre del archivo**, escriba `SampleImportScript.sql`, anote la ubicación donde guardará el archivo y, a continuación, elija el botón **Guardar**.  
  
7.  En la barra de menú, elija **Archivo**, **Cerrar solución**.  
  
     A continuación, cree un proyecto de base de datos e importe el esquema a partir del script que ha creado.  
  
##  <a name="CreateProject"></a> Crear un proyecto de base de datos e importar un esquema  
  
#### Para crear un proyecto de base de datos  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En **Instalado**, expanda el nodo **Plantillas**, expanda el nodo **Otros lenguajes**, elija la categoría **SQL Server** y después elija la plantilla **Proyecto de base de datos de SQL Server**.  
  
    > [!NOTE]
    >  El nodo **Otros lenguajes** no aparece en ninguna de las instalaciones de Visual Studio.  
  
3.  En el cuadro **Nombre**, escriba `Base de datos pequeña`.  
  
4.  Active la casilla **Crear directorio para la solución** si aún no está activada.  
  
5.  Desactive la casilla **Agregar al control de código fuente** si aún no está desactivada y elija el botón **Aceptar**.  
  
     El proyecto de base de datos se crea y aparece en el **Explorador de soluciones**.  
  
     A continuación, importe el esquema de base de datos desde el script.  
  
#### Para importar un esquema de base de datos desde un script  
  
1.  En la barra de menús, elija **Proyecto**, **Importar**, **Script**.  
  
2.  En la página de bienvenida, revise el texto y elija el botón de **Siguiente**.  
  
3.  Elija el botón de opción **Un solo archivo** y, a continuación, **Examinar**.  
  
     Aparece el cuadro de diálogo **Importar archivo de script de SQL**.  
  
4.  Abra la carpeta donde guardó el archivo SampleImportScript.sql, elíjalo y después elija el botón de **Abrir**.  
  
5.  Elija el botón **Finalizar** para cerrar el cuadro de diálogo **Importar archivo de script SQL**.  
  
     Se importa el script y los objetos que se definen en ese script se agregan al proyecto de base de datos.  
  
6.  Revise el resumen y elija el botón de **Finalizar** para cerrar el cuadro de diálogo de **Importar archivo de script SQL**.  
  
7.  En **Explorador de soluciones**, expanda las carpetas Ventas, Scripts y Seguridad de su proyecto y compruebe que contienen archivos .sql.  
  
8.  En **Explorador de objetos de SQL Server**, compruebe que la base de datos aparece bajo el nodo de **Proyectos**.  
  
     En este punto, la base de datos solo contiene objetos del sistema, como tablas y procedimientos almacenados.  Después de implementar la base de datos, contendrá las tablas y procedimientos almacenados de usuario que los scripts definen.  
  
##  <a name="DeployDatabase"></a> Implementar la base de datos  
 Al elegir la tecla F5, se implementa \(o publica\) la base de datos a una base de datos LocalDB de forma predeterminada.  Puede implementar la base de datos a una ubicación diferente abriendo la página de propiedades del proyecto, eligiendo la pestaña **Depurar** y después cambiando la cadena de conexión.