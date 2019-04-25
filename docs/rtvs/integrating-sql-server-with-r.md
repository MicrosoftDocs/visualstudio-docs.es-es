---
title: Integración de SQL Server con R
description: Visual Studio admite la creación y ejecución de consultas SQL en R y la posibilidad de que R trabaje con procedimientos almacenados.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: f15c785658b5c4cd5a6b158b05eb67ff9a4e4c2d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913985"
---
# <a name="work-with-sql-server-and-r"></a>Trabajar con SQL Server y R

La excelente compatibilidad de Visual Studio con SQL Server ayuda a los científicos de datos a trabajar con bases de datos SQL y R gracias a la posibilidad de crear y ejecutar consultas SQL, así como de trabajar con procedimientos almacenados.

> [!Note]
> Para trabajar con SQL y R juntos, debe tener instalado SQL Server Data Tools:
> - Visual Studio 2017: ejecute el instalador de Visual Studio y seleccione el almacenamiento de datos y la carga de trabajo de procesamiento, que incluye SQL Server Data Tools.
> - Visual Studio 2015: siga las instrucciones de [Descargar SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Ver un vídeo (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) de introducción a SQL Server y R (3m 03s). |

## <a name="create-and-run-sql-queries"></a>Crear y ejecutar consultas SQL

RTVS admite la adición de consultas SQL en proyectos de R, lo que le permite desarrollar de manera iterativa consultas SQL en un contexto independiente hasta que obtenga los resultados que está buscando.

Para agregar un archivo de consulta SQL, haga clic con el botón derecho en el proyecto en el Explorador de soluciones, seleccione **Agregar** > **Nuevo elemento** y seleccione el tipo de archivo **Consulta SQL**:

![Agregar un elemento de consulta SQL a un proyecto](media/sql-add-item.png)

Este comando abre el archivo en el editor de Transact-SQL de Visual Studio, que proporciona IntelliSense completo para SQL y la capacidad para ejecutar consultas. Para que estas características funcionen, necesita conectar una base de datos con el botón de conexión de la barra de herramientas del editor o intentar ejecutar una consulta (**Ctrl**+**Mayús**+**E**, que también funciona en una selección). En ambos casos se abre el cuadro de diálogo de conexiones:

![Cuadro de diálogo Conexión SQL](media/sql-connection-dialog.png)

Una vez que se ha establecido la conexión, puede ejecutar consultas y ver los resultados:

![Resultados de la consulta en la ventana SQL](media/sql-query-results.png)

El editor de Transact-SQL admite una variedad de otras características, como ver el plan de ejecución de la consulta y un depurador de consultas.
Para obtener más información, vea [Usar el Editor de Transact-SQL para editar y ejecutar scripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>Trabajar con procedimientos almacenados de SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 y versiones posteriores) le permite insertar y ejecutar código de R desde un procedimiento almacenado T-SQL. Puede ejecutar código de R en un equipo de SQL Server, trabajar en los datos devueltos de una consulta SQL y generar un conjunto de resultados SQL que pueda procesarse por SQL o devolverse al cliente.

En cambio, RTVS simplifica el difícil proceso propenso a errores de combinar código de R y SQL en una única instrucción SQL, como se describe en las secciones siguientes:

- [Agregar una conexión de base de datos](#add-a-database-connection)
- [Escribir y probar un procedimiento almacenado de SQL](#write-and-test-a-sql-stored-procedure)
- [Publicar un procedimiento almacenado de SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Ver un vídeo (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) de introducción a los procedimientos recomendados de SQL y R (6m 09s). |

### <a name="add-a-database-connection"></a>Agregar una conexión de base de datos

1. Seleccione **Herramientas de R** > **Datos** > **Agregar conexión de base de datos** para que aparezca el cuadro de diálogo **Propiedades de la conexión**. Aquí especifique el nombre del origen de datos (SQL Server en este caso), el nombre del servidor, el modo de autenticación y el nombre de la base de datos. Seleccione **Prueba de conexión** para comprobar su entrada antes de cerrar el cuadro de diálogo.

    ![Cuadro de diálogo Conexión SQL](media/sql-connection-string-dialog.png)

1. Una vez que haya hecho clic en **Aceptar** con una conexión válida, Visual Studio genera una cadena de conexión denominada `dbConnection` en un archivo *settings.R* nuevo. RTVS obtiene automáticamente (ejecuta) este archivo, por lo que puede usar la conexión inmediatamente de los scripts de R:

![Archivo Settings.R de SQL](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Escribir y probar un procedimiento almacenado de SQL

Para agregar un nuevo procedimiento almacenado de SQL, haga clic con el botón derecho en el proyecto, seleccione **Agregar** > **Nuevo elemento**, seleccione **SQL Stored Procedure with R** (Procedimiento almacenado de SQL con R) en la lista de plantillas, proporcione un nombre al archivo y haga clic en **Aceptar**. El nombre de archivo predeterminado es *SqlSProc.R*; para facilitar la lectura, se usa el nombre de archivo *StoredProcedure.R* en el resto de esta sección. Si tiene varios procedimientos almacenados, cada archivo debe tener un nombre de archivo único.

RTVS crea tres archivos para el procedimiento almacenado: un archivo *.R* para el código de R, un archivo *.Query.sql* para el código SQL y un archivo *.Template.sql* que combina los dos. Estos dos últimos aparecen en el Explorador de soluciones como elementos secundarios del archivo *.R*:

![Vista expandida del Explorador de soluciones del procedimiento almacenado de SQL con R](media/sql-solution-explorer-expanded.png)

El archivo *.R* (*StoredProcedure.R* en este ejemplo) es donde se escribe código de R. El contenido predeterminado es:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Simplemente, el código recibe un dataframe de R denominado `InputDataSet` y devuelve sus resultados en `OutputDataSet`, con el código de plantilla copiando únicamente la entrada en la salida.

> [!Note]
> Los nombres de estos dataframe se controlan mediante los parámetros `@input_data_1_name` y `@output_data_1_name` en la llamada para el procedimiento almacenado del sistema `sp_execute_external_script`. Para obtener más información sobre el diseño de esta convención de llamada y algunos ejemplos de su uso, vea [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

El otro código generado (en los comentarios) proporciona un pequeño script de prueba que usa el [paquete RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) para transmitir una instrucción SQL a SQL Server, ejecutarla y recuperar su conjunto de resultados como un dataframe de R. Puede quitar la marca de comentario de este código de prueba para escribir de manera interactiva su código de R en el conjunto de resultados que obtiene de SQL Server.

El archivo *.Query.sql* (*StoredProcedure.Query.sql* en este ejemplo) es donde escribe y prueba la consulta SQL que genera los datos para `InputDataSet`. Con este archivo *.sql*, el editor proporciona todas las características de Transact-SQL habituales.

Una vez que esté satisfecho con el código SQL, intégrelo con su código de R arrastrando el archivo *.sql* en el editor abierto para el archivo *.R*. En la imagen siguiente, *StoredProcedure.Query.sql* se ha arrastrado hasta el punto de *StoredProcedure.R*, después de la coma en `sqlQuery(channel, )`:

![Leer archivos SQL en la variable de cadena de R](media/sql-reference-sql-file-from-r.png)

Como puede ver, este sencillo paso genera automáticamente código de R para abrir el archivo *.sql*, leer su contenido en una cadena y pasarlo al paquete RODBC para enviarlo a SQL Server.

Ahora puede escribir de manera interactiva código de R que manipula el dataframe `InputDataSet` como quiera. Recuerde que solo puede seleccionar código de R en el editor y enviarlo a la [ventana interactiva](interactive-repl-for-r-in-visual-studio.md) presionando **Ctrl**+**Entrar**.

El archivo *.Template.sql* (*StoredProcedure.Template.sql* en este ejemplo), por último, contiene la plantilla para generar el procedimiento almacenado de SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- El marcador de posición `_RCODE_` se reemplaza por el contenido del archivo *.R* (por ejemplo, *StoredProcedure.R*).
- El marcador de posición `_INPUT_QUERY_` se reemplaza por el contenido del archivo *.Query.sql* (por ejemplo, *StoredProcedure.Query.sql*).
- Edite la cláusula `WITH RESULT SETS` para describir el esquema del conjunto de resultados devuelto desde el procedimiento almacenado. Identifique específicamente las columnas del dataframe `OutputDataSet` que quiera devolver al autor de la llamada del procedimiento almacenado.

Por ejemplo, para la consulta siguiente:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Usaría la siguiente cláusula `WITH RESULT SETS` para especificar los tipos de datos de los valores devueltos:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publicar un procedimiento almacenado de SQL

1. Seleccione el comando de menú **Herramientas de R** > **Datos** > **Publish With Options** (Publicar con opciones).
1. En el cuadro de diálogo que aparece, cambie **Publicar en:** por **Base de datos**, especifique el destino y seleccione **Publicar**; a continuación, RTVS crea y publica el procedimiento almacenado:

    ![Cuadro de diálogo Publicar procedimiento almacenado](media/sql-publish-with-options.png)

1. Para publicar todos los procedimientos almacenados de un proyecto, puede usar el comando **Herramientas de R** > **Datos** > **Publicar procedimientos almacenados**, que también está disponible cuando hace clic con el botón derecho en el proyecto en el Explorador de soluciones.

> [!Tip]
> Si tiene el Explorador de objetos de SQL Server abierto en Visual Studio, su procedimiento almacenado aparece publicado en la carpeta **Programación** > **Procedimientos almacenados** de su base de datos. También puede ejecutarlo desde el Explorador de objetos haciendo clic con el botón derecho y seleccionando **Ejecutar procedimiento**, o llamándolo de manera interactiva desde una ventana de consulta de *.sql*.
