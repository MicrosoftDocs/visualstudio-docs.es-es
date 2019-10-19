---
title: Actualizar archivos .mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e0196c582fbe673d73c7aeb89280d05e11a071a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639574"
---
# <a name="upgrade-mdf-files"></a>Actualizar archivos .mdf

En este tema se describen las opciones para actualizar un archivo de base de datos ( *. MDF*) después de instalar una versión más reciente de Visual Studio. Incluye instrucciones para las siguientes tareas:

- Actualizar un archivo de base de datos para usar una versión más reciente de SQL Server Express LocalDB

- Actualizar un archivo de base de datos para usar una versión más reciente de SQL Server Express

- Trabajar con un archivo de base de datos en Visual Studio, pero mantener la compatibilidad con una versión anterior de SQL Server Express o LocalDB

- Crear SQL Server Express el motor de base de datos predeterminado

Puede usar Visual Studio para abrir un proyecto que contenga un archivo de base de datos ( *. MDF*) creado con una versión anterior de SQL Server Express o LocalDB. Sin embargo, para continuar desarrollando el proyecto en Visual Studio, debe tener la versión de SQL Server Express o LocalDB instalada en el mismo equipo que Visual Studio, o bien debe actualizar el archivo de base de datos. Si actualiza el archivo de base de datos, no podrá tener acceso a él mediante versiones anteriores de SQL Server Express o LocalDB.

También es posible que se le pida que actualice un archivo de base de datos creado a través de una versión anterior de SQL Server Express o LocalDB si la versión del archivo no es compatible con la instancia de SQL Server Express o LocalDB instalada actualmente. Para resolver el problema, Visual Studio le pedirá que actualice el archivo.

> [!IMPORTANT]
> Se recomienda hacer una copia de seguridad del archivo de base de datos antes de actualizarlo.

> [!WARNING]
> Si actualiza un archivo *. MDF* creado en LocalDB 2014 (V12) 32 bit a LocalDB 2016 (v13) o posterior, no podrá volver a abrir el archivo en la versión de 32 bits de LocalDB.

Antes de actualizar una base de datos, tenga en cuenta los siguientes criterios:

- No actualice si desea trabajar en el proyecto en una versión anterior y en una versión más reciente de Visual Studio.

- No actualice si la aplicación se va a usar en entornos que usan SQL Server Express en lugar de LocalDB.

- No actualice si la aplicación usa conexiones remotas, ya que LocalDB no las acepta.

- No actualice si la aplicación se basa en Internet Information Services (IIS).

- Considere la posibilidad de actualizar si desea probar las aplicaciones de base de datos en un entorno de espacio aislado pero no desea administrar una base de datos.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Para actualizar un archivo de base de datos para usar la versión de LocalDB

1. En **Explorador de servidores**, seleccione el botón **conectar con base de datos** .

2. En el cuadro de diálogo **Agregar conexión** , especifique la información siguiente:

    - **Origen de datos**: `Microsoft SQL Server (SqlClient)`

    - **Nombre del servidor**:

        - Para usar la versión predeterminada: `(localdb)\MSSQLLocalDB`.  Esto especificará ProjectV12 o ProjectV13, en función de la versión de Visual Studio que esté instalada y de la creación de la primera instancia de LocalDB. El nodo **MSSQLLocalDB** de **Explorador de objetos de SQL Server** muestra la versión a la que apunta.

        - Para usar una versión específica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13`, donde V12 es LocalDB 2014 y v13 es LocalDB 2016.

    - **Adjunte un archivo de base de datos**: la ruta de acceso física del archivo *. MDF* principal.

    - **Nombre lógico**: el nombre que desea usar con el archivo.

3. Seleccione el botón **Aceptar**.

4. Cuando se le pida, seleccione el botón **sí** para actualizar el archivo.

    La base de datos se actualiza, se adjunta al motor de base de datos LocalDB y ya no es compatible con la versión anterior de LocalDB.

También puede modificar una conexión SQL Server Express para usar LocalDB; para ello, abra el menú contextual de la conexión y, a continuación, seleccione **modificar conexión**. En el cuadro de diálogo **modificar conexión** , cambie el nombre del servidor a `(LocalDB)\MSSQLLocalDB`. En el cuadro de diálogo **propiedades avanzadas** , asegúrese de que la **instancia de usuario** está establecida en **false**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Para actualizar un archivo de base de datos para que use la versión SQL Server Express

1. En el menú contextual para la conexión a la base de datos, seleccione **modificar conexión**.

2. En el cuadro de diálogo **modificar conexión** , seleccione el botón **Opciones avanzadas** .

3. En el cuadro de diálogo **propiedades avanzadas** , seleccione el botón **Aceptar** sin cambiar el nombre del servidor.

    El archivo de base de datos se actualiza para que coincida con la versión actual de SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Para trabajar con la base de datos en Visual Studio, pero conservar la compatibilidad con SQL Server Express

- En Visual Studio, abra el proyecto sin actualizarlo.

  - Para ejecutar el proyecto, seleccione la tecla **F5** .

  - Para editar la base de datos, abra el archivo *. MDF* en **Explorador de soluciones**y expanda el nodo en **Explorador de servidores** para trabajar con la base de datos.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Para que SQL Server Express el motor de base de datos predeterminado

1. En la barra de menús, seleccione **herramientas**  > **Opciones**.

2. En el cuadro de diálogo **Opciones** , expanda las opciones **herramientas de base** de **datos**y, a continuación, seleccione conexiones de datos.

3. En el cuadro de texto **nombre de instancia de SQL Server** , especifique el nombre de la instancia de SQL Server Express o LocalDB que desee usar. Si la instancia no tiene nombre, especifique `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4. Seleccione el botón **Aceptar**.

    SQL Server Express será el motor de base de datos predeterminado para las aplicaciones.

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](accessing-data-in-visual-studio.md)
