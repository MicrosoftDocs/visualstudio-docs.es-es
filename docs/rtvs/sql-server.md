---
title: Integrar SQL Server con las herramientas de R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>Trabajar con SQL Server y R

Herramientas de R para Visual Studio (RTVS) se aprovecha de la excelente compatibilidad de Visual Studio con SQL Server para facilitar a los científicos de datos el trabajo con bases de datos SQL, es decir, la creación de consultas SQL de ejecución y trabajar con procedimientos almacenados.

> [!Note]
> Para trabajar con SQL y R juntos, debe tener instalado SQL Server Data Tools:
> - Visual Studio 2017: ejecute el instalador de Visual Studio y seleccione el almacenamiento de datos y la carga de trabajo de procesamiento, que incluye SQL Server Data Tools.
> - Visual Studio 2015: siga las instrucciones de [Descargar SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

En el vídeo siguiente (3m 03s) se proporciona una breve información general de SQL Server y R:

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>Crear y ejecutar consultas SQL

RTVS admite la adición de consultas SQL en proyectos de R, lo que le permite desarrollar de manera iterativa consultas SQL en un contexto independiente hasta que obtenga los resultados que está buscando.

Para agregar un archivo de consulta SQL, haga clic con el botón derecho en el proyecto del Explorador de soluciones, seleccione **Agregar > Nuevo elemento...** y seleccione el tipo de archivo **Consulta SQL**:

![Agregar un elemento de consulta SQL a un proyecto](~/rtvs/media/sql-add-item.png)

Esto abre el archivo en el editor de Transact-SQL de Visual Studio, que proporciona IntelliSense completo para SQL y la capacidad para ejecutar consultas. En cambio, para que estas características funcionen, necesita conectar una base de datos con el botón de conexión de la barra de herramientas del editor o simplemente intentar ejecutar una consulta (Ctrl+Mayús+E, que también funciona en una selección). En ambos casos se abre el cuadro de diálogo de conexiones:

![Cuadro de diálogo Conexión SQL](~/rtvs/media/sql-connection-dialog.png)

Una vez que se ha establecido la conexión, puede ejecutar consultas y ver los resultados:

![Resultados de la consulta en la ventana SQL](~/rtvs/media/sql-query-results.png)

El editor de Transact-SQL admite una variedad de otras características, como ver el plan de ejecución de la consulta o un depurador de consultas. Existen muchas otras características disponibles con el editor de Transact-SQL. Para obtener información, vea [Usar el Editor de Transact-SQL para editar y ejecutar scripts](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Trabajar con procedimientos almacenados de SQL Server

[SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 y versiones posteriores) le permite insertar y ejecutar código de R desde un procedimiento almacenado T-SQL. Esto significa que puede ejecutar el equipo de SQL Server con código de R, trabajar en los datos devueltos de una consulta SQL y generar un conjunto de resultados SQL que pueda procesarse por SQL o devolverse al cliente.

En cambio, RTVS simplifica el difícil proceso propenso a errores de combinar código de R y SQL en una única instrucción SQL, como se describe en las secciones siguientes:

- [Agregar una conexión de base de datos](#add-a-database-connection)
- [Escribir y probar un procedimiento almacenado de SQL](#write-and-test-a-sql-stored-procedure)
- [Publicar un procedimiento almacenado de SQL](#publish-a-sql-stored-procedure)

En el vídeo siguiente (6m 09s) también se proporciona información general de estas características:

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>Agregar una conexión de base de datos

1. Seleccione **Herramientas de R > Datos > Agregar conexión de base de datos** para abrir el cuadro de diálogo **Propiedades de la conexión**, en el que especifica el nombre del origen de datos (SQL Server en este caso), el nombre del servidor, el modo de autenticación y el nombre de la base de datos. Puede seleccionar **Prueba de conexión** para comprobar su entrada antes de cerrar el cuadro de diálogo.
 
    ![Cuadro de diálogo Conexión SQL](~/rtvs/media/sql-connection-string-dialog.png)

1. Una vez que haya seleccionado **Aceptar** con una conexión válida, Visual Studio genera una cadena de conexión denominada `dbConnection` en un archivo `settings.R` nuevo. RTVS obtiene automáticamente (ejecuta) este archivo, por lo que puede usar la conexión inmediatamente de los scripts de R:

![Archivo Settings.R de SQL](~/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Escribir y probar un procedimiento almacenado de SQL

Para agregar un nuevo procedimiento almacenado de SQL, haga clic con el botón derecho en su proyecto, seleccione **Agregar > Nuevo elemento...**, seleccione **Procedimiento almacenado de SQL con R** de la lista de plantillas, proporcione un nombre al archivo (`StoredProcedure.R` en este ejemplo) y seleccione **Aceptar**.
 
RTVS crea tres archivos para el procedimiento almacenado, un archivo `.R` para su código de R, un archivo `.Query.sql` para el código SQL y un archivo `.Template.sql` que combina los dos. Estos dos últimos aparecen en el Explorador de soluciones como elementos secundarios del archivo `.R`:

![Vista expandida del Explorador de soluciones del procedimiento almacenado de SQL con R](~/rtvs/media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (en este ejemplo) es el lugar donde escribirá su código de R. El contenido predeterminado es el siguiente:

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
> Los nombres de estos dataframe se controlan mediante los parámetros `@input_data_1_name` y `@output_data_1_name` en la llamada para el procedimiento almacenado del sistema `sp_execute_external_script`. Para obtener más información sobre el diseño de esta convención de llamada y algunos ejemplos de su uso, [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

El otro código generado en los comentarios es un pequeño script de prueba que usa el [paquete RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) para transmitir una instrucción SQL a SQL Server, ejecutarla y recuperar su conjunto de resultados como un dataframe de R. Puede quitar la marca de comentario de este código de prueba para escribir de manera interactiva su código de R en el conjunto de resultados que obtiene de SQL Server.

`StoredProcedure.Query.sql` es donde escribe y prueba la consulta SQL que genera los datos para `InputDataSet`. Como es un archivo `.sql`, tiene todas las características del editor de Transact-SQL disponibles.

Una vez que esté satisfecho con el código SQL, puede integrarlo fácilmente con su código de R en `StoredProcedure.R` arrastrando simplemente el archivo `.sql` en el editor abierto para el archivo `.R`. En la imagen siguiente, `StoredProcedure.Query.sql` se ha arrastrado hasta el punto después de la coma en `sqlQuery(channel, )`:

![Leer archivos SQL en la variable de cadena de R](~/rtvs/media/sql-reference-sql-file-from-r.png)

Como puede ver, este sencillo paso genera automáticamente código de R para abrir el archivo `.sql`, leer su contenido en una cadena y pasarlo al paquete RODBC para enviarlo a SQL Server.

De este modo, ahora puede escribir código de R de manera interactiva que manipula el dataframe `InputDataSet` como quiera. Recuerde que solo puede seleccionar código de R en el editor y enviarlo a la [ventana interactiva](interactive-repl.md) presionando Ctrl+Entrar.

Por último, `StoredProcedure.Template.sql` contiene la plantilla para generar su procedimiento almacenado de SQL:

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

- El marcador de posición `_RCODE_` se reemplaza por el contenido de `StoredProcedure.R`.
- El marcador de posición `_INPUT_QUERY_` se reemplaza por el contenido de `StoredProcedure.Query.sql`.
- Necesita describir el esquema del conjunto de resultados devuelto del procedimiento almacenado editando la cláusula `WITH RESULT SETS`. Identifique específicamente las columnas del dataframe `OutputDataSet` que quiera devolver al autor de la llamada del procedimiento almacenado. 

Por ejemplo, para la consulta siguiente:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Usaría la siguiente cláusula `WITH RESULT SETS` para especificar los tipos de datos de los valores devueltos:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publicar un procedimiento almacenado de SQL

1. Seleccione el comando de menú **Herramientas de R > Datos > Publicar con opciones...**.
1. En el cuadro de diálogo que aparece, cambie **Publicar en:** por **Base de datos**, especifique el destino, seleccione **Publicar** y RTVS creará y publicará el procedimiento almacenado:

    ![Cuadro de diálogo Publicar procedimiento almacenado](~/rtvs/media/sql-publish-with-options.png)

1. Para publicar todos los proyectos almacenados de un proyecto, también puede usar el comando **Herramientas de R > Datos > Publicar procedimientos almacenados**, que también está disponible cuando haga clic con el botón derecho en el proyecto del Explorador de soluciones.

> [!Tip]
> Si tiene el Explorador de objetos de SQL Server abierto en Visual Studio, también verá su procedimiento almacenado publicado en la carpeta **Programación > Procedimientos almacenados** de su base de datos. También puede ejecutarlo desde el Explorador de objetos haciendo clic con el botón derecho y seleccionando **Ejecutar procedimiento**, o llamándolo de manera interactiva desde una ventana de consulta de `.sql`.

