---
title: Instalación de SQL Server bases de datos de ejemplo | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299627"
---
# <a name="install-sql-server-sample-databases"></a>Instalación de bases de datos de ejemplo de SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las bases de datos de ejemplo son útiles para experimentar con consultas SQL y LINQ, el enlace de datos, el modelado de Entity Framework, etc.  Cada producto de base de datos tiene sus propias bases de datos de ejemplo. Northwind y AdventureWorks son dos conocidas SQL Server bases de datos de ejemplo.

 **AdventureWorks** es la base de datos de ejemplo actual proporcionada para SQL Server productos. Puede descargarlo como un archivo. MDF de la [Página de AdventureWorks en Codeplex](https://archive.codeplex.com/?p=msftdbprodsamples). Hay versiones normales y ligeras (LT) de la base de datos disponibles aquí. Para la mayoría de los escenarios, se prefiere la versión LT porque es menos compleja.

 **Northwind** es una base de datos de SQL Server relativamente sencilla que se ha usado durante muchos años. Puede descargarlo como un archivo. bak desde la [Página de base de datos Northwind en Codeplex](https://northwinddatabase.codeplex.com/). Para evitar problemas de permisos, descomprima el archivo en una carpeta nueva que no esté bajo su carpeta de usuario.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Para restaurar una base de datos desde un archivo. bak en Visual Studio

1. Al realizar una copia de seguridad de una base de datos de Microsoft SQL Server, el resultado es un archivo. bak. Para que el archivo. bak se pueda volver a usar como un archivo de base de datos, debe *restaurarse*. En el menú principal, seleccione **ver** > **Explorador de objetos de SQL Server**. Si no lo ve, es posible que tenga que instalarlo. Vaya al **Panel de Control** > **programas y características**, busque Microsoft Visual Studio 2015 y haga clic en el botón **cambiar** . Cuando aparezca la lista de componentes instalados en la ventana del instalador, active la casilla **Explorador de objetos de SQL Server** y, a continuación, continúe con la instalación.

2. En Explorador de objetos de SQL Server, haga clic con el botón secundario en cualquier motor de base de datos SQL Server (por ejemplo, LocalDB) y seleccione**nueva consulta**.

     ![Explorador de objetos de SQL Server nueva consulta](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Explorador de objetos de SQL Server nueva consulta")

3. En primer lugar, necesita los nombres lógicos de la base de datos y los archivos de registro dentro del archivo. bak. Para obtenerla, escriba esta consulta en el editor de consultas de SQL y, a continuación, seleccione el botón verde **Ejecutar** situado en la parte superior de la ventana. Modifique la ruta de acceso del archivo, si es necesario, para que apunte al archivo. bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Anote los nombres lógicos que aparecen en la ventana resultados.  En la base de datos Northwind, los dos nombres lógicos son Northwind y Northwind_log.

4. Ahora ejecute esta consulta para crear la base de datos. Sustituya las rutas de acceso de origen y de destino, los nombres de base de datos lógicos y los nombres de archivo físicos de Northwind según corresponda. Mantenga las extensiones de archivo. MDF y. ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. En Explorador de objetos de SQL Server, haga clic con el botón secundario en el nodo **bases** de datos y debería ver el nodo base de datos Northwind. Si no es así, haga clic con el botón derecho en bases de datos y seleccione **Agregar nueva base de datos**. Escriba el nombre y la ubicación del archivo. MDF que acaba de crear.

6. La base de datos ya está lista para usarse como origen de datos en Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Para restaurar una base de datos desde un archivo. bak en SQL Server Management Studio

1. Descargue SQL Server Management Studio del sitio de descarga.

2. En la ventana **Explorador de objetos** de SSMS, haga clic con el botón secundario en el nodo **bases** de datos, seleccione**restaurar base de datos**y proporcione la ubicación del archivo. bak.

     ![Base de datos de restauración de SSMS](../data-tools/media/raddata-ssms-restore-database.png "Base de datos de restauración de raddata SSMS")
