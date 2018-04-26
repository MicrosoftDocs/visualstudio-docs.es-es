---
title: Actualizar los archivos .mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fa7fac39e8f198c473bf79a68a48feb136eccda3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="upgrade-mdf-files"></a>Actualizar los archivos .mdf

En este tema se describe las opciones de actualización de un archivo de base de datos (.mdf) después de instalar una versión más reciente de Visual Studio. Incluye instrucciones para las tareas siguientes:

- Actualizar un archivo de base de datos para utilizar una versión más reciente de SQL Server Express LocalDB

- Actualizar un archivo de base de datos para utilizar una versión más reciente de SQL Server Express

- Trabajar con un archivo de base de datos en Visual Studio, pero mantener la compatibilidad con una versión anterior de SQL Server Express o LocalDB

- Hacer que SQL Server Express el motor de base de datos predeterminada

Puede usar Visual Studio para abrir un proyecto que contiene un archivo de base de datos (.mdf) que se creó con una versión anterior de SQL Server Express o LocalDB. Sin embargo, para continuar desarrollando el proyecto en Visual Studio, debe tener esa versión de SQL Server Express o LocalDB instalada en el mismo equipo que Visual Studio, o debe actualizar el archivo de base de datos. Si actualiza el archivo de base de datos, no podrá obtener acceso a él mediante el uso de las versiones anteriores de SQL Server Express o LocalDB.

También se pedirá para actualizar un archivo de base de datos que se creó a través de una versión anterior de SQL Server Express o LocalDB si la versión del archivo no es compatible con la instancia de SQL Server Express o LocalDB instalada actualmente. Para resolver el problema, Visual Studio le pedirá que se actualice el archivo.

> [!IMPORTANT]
> Se recomienda que haga una copia del archivo de base de datos antes de que la actualización.

> [!WARNING]
> Si actualiza un archivo .mdf que se creó en LocalDB 2014 (V12) de 32 bits a LocalDB 2016 (versión 13) o posterior, no podrá volver a abrir el archivo en la versión de 32 bits de LocalDB.

Antes de actualizar una base de datos, tenga en cuenta los siguientes criterios:

-   No realiza la actualización si desea trabajar en el proyecto en una versión anterior y una versión más reciente de Visual Studio.

-   No realiza la actualización si la aplicación va a utilizar en entornos que usan SQL Server Express en lugar de LocalDB.

-   No realiza la actualización si la aplicación utiliza las conexiones remotas, porque LocalDB no los acepta.

-   No realiza la actualización si la aplicación se basa en Internet Information Services (IIS).

-   Considere la posibilidad de actualizar si desea probar las aplicaciones de base de datos en un entorno de espacio aislado, pero no desea administrar una base de datos.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Para actualizar un archivo de base de datos para utilizar la versión de LocalDB

1.  En **Explorador de servidores**, seleccione la **conectar con base de datos** botón.

2.  En el **Agregar conexión** diálogo cuadro, especifique la siguiente información:

    -   **Origen de datos**: `Microsoft SQL Server (SqlClient)`

    -   **Nombre del servidor**:

        -   Para usar la versión predeterminada: `(localdb)\MSSQLLocalDB`.  Esto permitirá especificar ProjectV12 o ProjectV13, dependiendo de qué versión de Visual Studio está instalado y cuando se creó la primera instancia de LocalDB. El **MSSQLLocalDB** nodo **Explorador de objetos de SQL Server** muestra qué versión que apunta al.

        -   Para usar una versión específica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13`, donde V12 es LocalDB 2014 y V13 es LocalDB 2016.

    -   **Adjuntar un archivo de base de datos**: la ruta de acceso física del archivo .mdf principal.

    -   **Nombre lógico**: el nombre que desea usar con el archivo.

3.  Seleccione el botón **Aceptar**.

4.  Cuando se le pida, seleccione la **Sí** botón para actualizar el archivo.

    La base de datos se actualiza, se adjunta al motor de base de datos LocalDB y ya no es compatible con la versión anterior de LocalDB.

También puede modificar una conexión de SQL Server Express para utilizar LocalDB abriendo el menú contextual de la conexión y, a continuación, seleccionando **modificar conexión**. En el **modificar conexión** diálogo cuadro, cambie el nombre del servidor para `(LocalDB)\MSSQLLocalDB`. En el **propiedades avanzadas** diálogo cuadro, asegúrese de que **User Instance** está establecido en **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Para actualizar un archivo de base de datos para utilizar la versión de SQL Server Express

1.  En el menú contextual para la conexión a la base de datos, seleccione **modificar conexión**.

2.  En el **modificar conexión** cuadro de diálogo, seleccione la **avanzadas** botón.

3.  En el **propiedades avanzadas** cuadro de diálogo, seleccione la **Aceptar** botón sin cambiar el nombre del servidor.

    El archivo de base de datos se actualiza para que coincida con la versión actual de SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Para trabajar con la base de datos en Visual Studio, pero conservar la compatibilidad con SQL Server Express

-   En Visual Studio, abra el proyecto sin actualizarla.

    -   Para ejecutar el proyecto, seleccione la **F5** clave.

    -   Para editar la base de datos, abra el archivo .mdf en **el Explorador de soluciones**y expanda el nodo en **Explorador de servidores** para trabajar con la base de datos.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Para hacer que SQL Server Express el motor de base de datos predeterminada

1.  En la barra de menús, seleccione **herramientas**, **opciones**.

2.  En el **opciones** cuadro de diálogo, expanda el **herramientas de base de datos** opciones y, a continuación, seleccione **las conexiones de datos**.

3.  En el **nombre de instancia de SQL Server** texto, especifique el nombre de la instancia de SQL Server Express o LocalDB que se va a utilizar. Si no se denomine la instancia, especifique `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4.  Seleccione el botón **Aceptar**.

    SQL Server Express será el motor de base de datos predeterminado para las aplicaciones.

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](accessing-data-in-visual-studio.md)