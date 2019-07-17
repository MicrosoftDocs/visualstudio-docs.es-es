---
title: Instalar bases de datos de ejemplo de SQL Server | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 056e5d1fad258d063e30cfd97e85529ff3a0c9bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160187"
---
# <a name="install-sql-server-sample-databases"></a>Instalación de bases de datos de ejemplo de SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las bases de datos son útiles para experimentar con consultas SQL y LINQ, enlace de datos, modelado de Entity Framework y así sucesivamente.  Cada producto de base de datos tiene sus propias bases de datos de ejemplo. AdventureWorks y Northwind son dos populares bases de datos de ejemplo SQL Server.  
  
 **AdventureWorks** es la actual base de datos de ejemplo proporcionado para productos de SQL Server. Puede descargarlo como un archivo .mdf de la [página AdventureWorks en Codeplex](http://msftdbprodsamples.codeplex.com/). Hay normales y ligeras (LT) las versiones de la base de datos disponibles aquí. Para la mayoría de los escenarios, la versión LT es preferible porque es menos complejo.  
  
 **Northwind** es una base de datos de SQL Server relativamente sencilla que se ha usado durante muchos años. Puede descargarlo como un archivo .bak desde el [página de base de datos Northwind en CodePlex](https://northwinddatabase.codeplex.com/). Para evitar problemas de permisos, descomprima el archivo en una carpeta nueva que no esté bajo su carpeta de usuario.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Para restaurar una base de datos desde un archivo .bak en Visual Studio  
  
1. Realizar una copia de una base de datos de Microsoft SQL Server, el resultado es un archivo .bak. Para realizar la .bak archivo utilizable nuevo como un archivo de base de datos, debe ser *restaurar*. En el menú principal, seleccione **vista** > **Explorador de objetos de SQL Server**. Si no lo ve, es posible que deba instalarlo. Vaya a **Panel de Control** > **programas y características**, busque Microsoft Visual Studio 2015 y haga clic en el **cambio** botón. Cuando aparezca la lista de los componentes instalados en la ventana del instalador, seleccione el **Explorador de objetos de SQL Server** casilla de verificación y, a continuación, continúe con la instalación.  
  
2. En el Explorador de objetos de SQL Server, haga clic en cualquier motor de base de datos de SQL Server (por ejemplo, localdb) y seleccione**nueva consulta**.  
  
     ![Objeto Explorer nueva consulta de SQL Server](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata objeto Explorer nueva consulta de SQL Server")  
  
3. En primer lugar, necesita los nombres lógicos de los archivos de base de datos y registro dentro del archivo .bak. Para obtenerla, escriba esta consulta en el Editor de consultas SQL y, a continuación, seleccione el color verde **ejecutar** situado en la parte superior de la ventana. Si es necesario para que apunte al archivo .bak, modifique la ruta de acceso de archivo.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Anote los nombres lógicos que aparecen en la ventana de resultados.  Para la base de datos Northwind, los dos nombres lógicos son Northwind y Northwind_log.  
  
4. Ahora, ejecute esta consulta para crear la base de datos. Sustituya sus propias rutas de acceso de origen y destino, los nombres de base de datos lógica y los nombres de archivo físico para Northwind según corresponda. Mantener los archivos .mdf y .ldf extensiones de archivo.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5. En el Explorador de objetos de SQL Server, haga doble clic en el **bases de datos** nodo y debería ver el nodo de base de datos Northwind. Si no, a continuación, haga doble clic en las bases de datos y seleccione **agregar nueva base de datos**. Escriba el nombre y la ubicación del archivo .mdf que acaba de crear.  
  
6. La base de datos ahora está listo para usar como origen de datos en Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Para restaurar una base de datos desde un archivo .bak en SQL Server Management Studio  
  
1. Descargar SQL Server Management Studio desde el sitio de descarga.  
  
2. En SSMS **Explorador de objetos** ventana, haga clic en el **bases de datos** nodo, seleccione**Restore Database**y proporcionar la ubicación del archivo .bak.  
  
     ![Restaurar base de datos SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS Restaurar base de datos")
