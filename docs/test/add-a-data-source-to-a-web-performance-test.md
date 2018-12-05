---
title: Adición de un origen de datos a una prueba de rendimiento web en Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 13d0f405b59b95df0edbcfc5e6f051c1f3140035
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896112"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Agregar un origen de datos a una prueba de rendimiento web

Utilice el enlace datos para proporcionar valores diferentes a la misma prueba; por ejemplo, para proporcionar valores diferentes a los parámetros de envío de formulario.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Enlazar datos a una prueba de rendimiento web](../test/media/web_test_databinding_conceptual.png)

Vamos a utilizar una aplicación ASP.NET de ejemplo. Tiene tres páginas *.aspx*: la página predeterminada, la página Red y la página Blue. La página predeterminada tiene un control de radio para elegir entre rojo y azul y un botón de envío. Las otras dos páginas *.aspx* son muy simples. Una tiene una etiqueta denominada Red y la otra tiene una etiqueta denominada Blue. Cuando elige Submit en la página predeterminada, se muestra una de las otras páginas. Puede descargar el ejemplo [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) o sencillamente seguir con su propia aplicación web.

![Ejecutar la aplicación web que se va a probar](../test/media/web_test_databinding_runwebapp.png)

La solución también debe incluir una prueba de rendimiento web que examine las páginas de la aplicación web.

![Solución con prueba de rendimiento web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Crear una base de datos SQL

1. Si no tiene Visual Studio Enterprise, puede descargarlo desde la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

2. Cree una base de datos SQL.

     ![Agregar una nueva base de datos SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Cree un proyecto de base de datos.

     ![Crear nuevo proyecto a partir de una base de datos](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Agregar una tabla al proyecto de base de datos.

     ![Agregar una nueva tabla al proyecto de base de datos](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Agregue campos a la tabla.

     ![Agregar campos a la tabla](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publique el proyecto de base de datos.

     ![Publicar proyecto de base de datos del Explorador de soluciones](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Agregue datos a los campos.

     ![Agregar datos a los campos](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

## <a name="add-the-data-source"></a>Agregar el origen de datos

1. Agregue un origen de datos.

     ![Agregar origen de datos a la prueba de rendimiento web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Elija el tipo de origen de datos y asígnele un nombre.

     ![Dar un nombre al origen de la base de datos](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Cree una conexión.

     ![Elegir nueva conexión](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Especifique los detalles de la conexión.

     ![Especificar las propiedades de conexión de la base de datos SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Seleccione la tabla que desea usar para la prueba.

     ![Agregar la tabla Color como origen de datos](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     La tabla está enlazada a la prueba.

     ![Adición del nodo Orígenes de datos a la prueba de rendimiento web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Guarde la prueba.

## <a name="bind-the-data"></a>Enlazar los datos

1. Enlace el campo **ColorName**.

     ![Enlazar el campo ColorName al valor RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Abra el archivo *Local.testsettings* en el **Explorador de soluciones** y seleccione la opción **Una ejecución por fila de origen de datos**.

     ![Edite el archivo de configuración de pruebas.](../test/media/web_test_databinding_sql_testsettings.png)

3. Guarde la prueba de rendimiento web.

## <a name="run-the-test-with-the-data"></a>Ejecutar la prueba con los datos

1. Ejecute la prueba.

     ![Ejecutar la prueba de rendimiento web para comprobar los enlaces](../test/media/web_test_databinding_sql_runtest.png)

     Se muestran las dos ejecuciones de cada fila de datos. La ejecución 1 envía una solicitud para la página *Red.aspx*, mientras que la ejecución 2 envía una solicitud para la página *Blue.aspx*.

     ![Resultados de las series de pruebas](../test/media/web_test_databinding_sql_runresults.png)

     Cuando establece un enlace con un origen de datos, puede infringir la regla de dirección URL de respuesta predeterminada. En este caso, el error de la ejecución 2 estará causado por la regla que espera la página *Red.aspx* de la grabación de la prueba original; pero el enlace de datos ahora dirige a la página *Blue.aspx*.

2. Corrija el error de validación eliminando la regla de validación de la **dirección URL de respuesta** y vuelva a ejecutar la prueba.

     ![Eliminar la regla de validación de dirección URL de respuesta](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Ahora la prueba de rendimiento web se realiza correctamente utilizando el enlace de datos.

     ![La prueba se supera usando el enlace de datos](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Preguntas y respuestas

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>P: ¿Qué bases de datos puedo usar como origen de datos?

**R:** Puede usar las siguientes:

- Microsoft SQL Azure.

- Cualquier versión de Microsoft SQL Server 2005 o posterior.

- Un archivo de base de datos de Microsoft SQL Server (incluido SQL Express).

- Microsoft ODBC.

- Un archivo de Microsoft Access que utilice el proveedor de datos .NET Framework para OLE DB.

- Oracle 7.3, 8i, 9i o 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>P: ¿Puedo usar un archivo de texto de valores separados por comas (CSV) como origen de datos?

**R:** Aquí se explica cómo:

1. Cree una carpeta para organizar los artefactos de base de datos de los proyectos y agregar un elemento.

     ![Agregar nuevo elemento a la carpeta de datos](../test/media/web_test_databinding_foldernewitem.png)

2. Crear un archivo de texto

     ![Dar el nombre ColorData.csv al nuevo archivo de texto](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edite el archivo de texto y agregue lo siguiente:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Siga los pasos de [Agregar el origen de datos](#add-the-data-source), pero elija el archivo CSV como origen de datos.

     ![Especificar un nombre y elegir el archivo CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>P: ¿Qué ocurre si mi archivo CSV existente no contiene encabezados de columna?

**R:** Si no puede agregar encabezados de columna, puede usar un archivo de descripción de esquema para tratar el archivo CSV como una base de datos.

1. Agregue un nuevo archivo de texto denominado *schema.ini*.

     ![Agregar un archivo schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Edite el archivo *schema.ini* para agregar información que describa la estructura de los datos. Por ejemplo, un archivo de esquema que describa el archivo CSV podría ser similar al siguiente:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Agregue un origen de datos a la prueba.

     ![Agregar origen de datos a la prueba de rendimiento web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Si usa un archivo *schema.ini*, elija **Base de datos** (y no el archivo CSV) como origen de datos y asígnele un nombre.

     ![Agregar origen de datos de base de datos](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Cree una nueva conexión.

     ![Elegir nueva conexión](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Seleccionar el proveedor de datos .NET Framework para OLE DB.

     ![Seleccionar el proveedor de datos de .NET Framework para OLE DB](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Elija **Avanzado**.

     ![Elegir Avanzadas](../test/media/web_test_databinding_advanced.png)

8. En la propiedad Proveedor, seleccione Microsoft.Jet.OLEDB.4.0 y después establezca **Propiedades extendidas** en Text;HDR=NO.

     ![Aplicar propiedades avanzadas](../test/media/web_test_databinding_advancedproperties.png)

9. Escriba el nombre de la carpeta que contiene el archivo de esquema y pruebe la conexión.

     ![Especificar la ruta de acceso a la carpeta de datos](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Seleccione el archivo CSV que desee utilizar.

     ![Seleccionar el archivo de texto](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Cuando termine, el archivo CSV aparecerá como una tabla.

     ![Origen de datos agregado a la prueba](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>P: ¿Cómo utilizo un archivo XML como origen de datos?

**R:** Sí.

1. Cree una carpeta para organizar los artefactos de base de datos de los proyectos y agregar un elemento.

     ![Agregar nuevo elemento a la carpeta de datos](../test/media/web_test_databinding_foldernewitem.png)

2. Cree un archivo XML.

     ![Agregar el archivo ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Edite el archivo XML y agregue los datos:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Siga los pasos de [Agregar el origen de datos](#add-the-data-source), pero elija el archivo XML como origen de datos.

     ![Especificar un nombre y elegir el archivo XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>P: ¿Se puede agregar un enlace de datos a una solicitud de servicio Web que use SOAP?

**R:** Sí, debe cambiar manualmente el código XML de SOAP.

1. Elija la solicitud de servicio Web en el árbol de solicitudes y, en la ventana Propiedades, elija los puntos suspensivos (...) de la propiedad Texto de la cadena.

     ![Editar el cuerpo de la cadena del servicio Web](../test/media/web_test_databinding_webservicerequest.png)

2. Reemplace los valores del cuerpo SOAP por valores enlazados a datos con la siguiente sintaxis:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Por ejemplo, si tiene el siguiente código:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Puede cambiarlo por lo siguiente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Guarde la prueba.