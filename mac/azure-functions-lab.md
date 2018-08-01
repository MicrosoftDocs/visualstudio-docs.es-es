---
title: 'Tutorial: Azure Functions'
description: Uso de Azure Functions en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 53684537d20b483f74cbc270e988b130df3ba8c8
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232294"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Tutorial: Introducción a Azure Functions

En esta práctica aprenderá a empezar a compilar Azure Functions mediante Visual Studio para Mac. También podrá integrar con tablas de almacenamiento de Azure, que representan uno de los muchos tipos de enlaces y desencadenadores disponibles para los desarrolladores de Azure Functions.

## <a name="objectives"></a>Objetivos

> [!div class="checklist"]
> * Crear y depurar Azure Functions locales
> * Integrar con recursos web y de almacenamiento de Azure
> * Organizar un flujo de trabajo que implica varias Azure Functions

## <a name="requirements"></a>Requisitos

- Visual Studio para Mac 7.5 o posterior.
- Una suscripción de Azure (disponible gratis desde [https://azure.com/free](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Ejercicio 1: Crear un proyecto de Azure Functions

1. Inicie **Visual Studio para Mac**.

1. Seleccione **Archivo > Nueva solución**.

1. Desde la categoría **Nube > General**, seleccione la plantilla **Azure Functions**. Usará C# para crear una biblioteca de clases de .NET que hospede las Azure Functions. Haga clic en **Siguiente**.

    ![selección de plantilla de Azure Functions](media/azure-functions-lab-image1.png)

1. Establezca el **nombre del proyecto** en **"AzureFunctionsLab"** y haga clic en **Crear**.

    ![nombrar y crear el proyecto de azure function](media/azure-functions-lab-image2.png)

1. Expanda los nodos de **Panel de solución**. La plantilla de proyecto predeterminada incluye referencias de NuGet para una variedad de paquetes de AzureWebJobs, así como el paquete Newtonsoft.Json. 

     Hay también tres archivos:  
        - **host.JSON** para describir las opciones de configuración global del host  
        - **local.Settings.JSON** para configurar las opciones de servicio.  
        La plantilla de proyecto también crea un valor HttpTrigger predeterminado. Para los fines de esta práctica, debe eliminar el archivo **HttpTrigger.cs** desde el proyecto.  

    Abra **local.settings.json**. De forma predeterminada, tiene dos valores de cadena de conexión vacíos.

    ![panel de solución que muestra el archivo local.settings.json](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Ejercicio 2: Crear una cuenta de almacenamiento de Azure

1. Inicie sesión en su cuenta de Azure en [https://portal.azure.com](https://portal.azure.com).
 
1. En la sección **Favoritos**, situada a la izquierda de la pantalla, seleccione **Cuentas de almacenamiento**:

    ![sección Favoritos de Azure Portal que muestra el elemento Cuentas de almacenamiento](media/azure-functions-lab-image4.png)

1. Seleccione **Agregar** para crear una nueva cuenta de almacenamiento:

    ![Botón para agregar nueva cuenta de almacenamiento](media/azure-functions-lab-image5.png)

1. Escriba un nombre único global para el **nombre** y vuelva a usarlo para el **grupo de recursos**. Puede mantener todos los demás elementos como los predeterminados.

    ![detalles de nueva cuenta de almacenamiento](media/azure-functions-lab-image6.png)

1. Haga clic en **Crear**. Podría tardar unos minutos en crear la cuenta de almacenamiento. Recibirá una notificación cuando se haya creado correctamente.

    ![notificación de implementación correcta](media/azure-functions-lab-image7.png)

1. Seleccione el botón **Ir al recurso** de la notificación.

1. Seleccione la pestaña **Claves de acceso**.

    ![configuración de clave de acceso](media/azure-functions-lab-image8.png)

1. Copie la primera **cadena de conexión**. Esta cadena se usa para integrar el almacenamiento de Azure con Azure Funciones más adelante.

    ![información para la clave 1](media/azure-functions-lab-image9.png)

1. Vuelva a **Visual Studio para Mac** y pegue la cadena de conexión completa como en la configuración de **AzureWebJobsStorage** en **local.settings.json**. Ahora puede hacer referencia al nombre de la configuración en los atributos para funciones que necesitan acceder a sus recursos.

    ![archivo de configuración local con la clave de conexión especificada](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Ejemplo 3: Crear y depurar una función de Azure

1. Ahora está listo para comenzar a agregar el código. Cuando se trabaja con una biblioteca de clases .NET, Azure Functions se agrega como métodos estáticos. En **Panel de solución**, haga clic con el botón derecho en el nodo de proyecto **AzureFunctions** y seleccione **Agregar > Agregar función...**:

    ![Opción Agregar función](media/azure-functions-lab-image11.png)

1. En el cuadro de diálogo New Azure Functions (Nuevo Azure Functions), seleccione Generic webhook template (Plantilla de webhook genérica). Establezca el **nombre** que va a **agregar** y haga clic en **Aceptar** para crear la función:

    ![Cuadro de diálogo New Azure functions (Nuevas funciones de Azure)](media/azure-functions-lab-image12.png)

1. En la parte superior del nuevo archivo, agregue las directivas siguientes **using**:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Quite el método `Run` existente y agregue el método siguiente a la clase como la función de Azure:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```
1. Analicemos la definición del método parte por parte. 
    
    Lo primero que verá es el atributo **FunctionName** que marca este método como una función de Azure. El atributo designa el nombre público de la función. El nombre del atributo no tiene que coincidir con el nombre real del método.

    ![Nuevo método de ejecución con el atributo FunctionName resaltado](media/azure-functions-lab-image13.png)

1. Después, el método se marca como un método **estático público**, que es necesario. También observará que el valor devuelto es un **int**. A menos que especifique lo contrario al usar los atributos de método, cualquier valor devuelto distinto de void de una función de Azure se devuelve al cliente como texto. De forma predeterminada se devuelve como **XML**, pero puede cambiarse a **JSON**, lo cual lo hará más adelante en esta práctica.

    ![Nuevo método de ejecución con la inicialización del método resaltada](media/azure-functions-lab-image14.png)

1. El primer parámetro se marca con el atributo **HttpTrigger**, que indica que este método lo invoca una solicitud HTTP. El atributo también especifica el nivel de autorización del método, así como los verbos que admite (solo **"GET"**, en este caso). Opcionalmente, también puede definir una **ruta** que reemplaza la ruta de acceso al método y proporciona una manera de extraer automáticamente las variables de la ruta de acceso. Puesto que, en este caso, la **ruta** es null, la ruta de acceso a este método tendrá como valor predeterminado **/api/Add**.

    ![Nuevo método de ejecución con el parámetro resaltado](media/azure-functions-lab-image15.png)

1. El último parámetro para el método es un **TraceWriter** que se puede utilizar para registrar los mensajes de diagnóstico y errores.

    ![Nuevo método de ejecución con TraceWriter resaltado](media/azure-functions-lab-image16.png)

1. Establezca un punto de interrupción en la línea de **retorno** del método haciendo clic en el margen de la línea:

    ![Punto de interrupción establecido en línea de retorno](media/azure-functions-lab-image17.png)

1. Compile y ejecute el proyecto en una sesión de depuración presionando **F5** o seleccionando **Ejecutar > Iniciar depuración**. También puede hacer clic en el botón **Ejecutar**. Todas estas opciones realizan la misma tarea. El resto de esta práctica hace referencia a **F5**, pero puede utilizar el método que le resulte más cómodo.

    ![Compilar y ejecutar el proyecto](media/azure-functions-lab-image18.png)

1. Al ejecutar el proyecto se abrirá automáticamente la aplicación Terminal.

1. El proyecto lleva a cabo un proceso de detección de funciones de Azure que se basan en atributos de método y una convención de archivos que se trata más adelante en este artículo. En este caso, detecta una única función de Azure y "genera" 1 función de trabajo.

    ![Salida de la función de Azure en Terminal](media/azure-functions-lab-image19.png)

1. En la parte inferior de los mensajes de inicio, el host de Azure Functions imprime las direcciones URL de cualquier API de desencadenador HTTP. Solo debería haber una. Copie esa dirección URL y péguela en una nueva pestaña de explorador.

    ![URL de la API de la función de Azure](media/azure-functions-lab-image20.png)

1. El punto de interrupción debería desencadenarse inmediatamente. La solicitud web se ha enrutado a la función y ahora se puede depurar. Mueva el mouse sobre la variable **x** para ver su valor. 

    ![Punto de interrupción desencadenado](media/azure-functions-lab-image21.png)

1. Quite el punto de interrupción con el mismo método que usó para agregarlo anteriormente (haga clic en el margen o seleccione la línea y presione **F9**).

1. Presione **F5** para continuar la ejecución.

1. En el explorador, se representará el resultado XML del método. Como se esperaba, la operación de suma codificada de forma rígida genera una suma plausible. Si solo ve "3" en Safari, vaya a **Safari > Preferencias > Opciones avanzadas** y marque la casilla "**Show Develop menu in menu bar**" (Mostrar menú Desarrollo en la barra de menús) y vuelva a cargar la página.

1. En **Visual Studio para Mac**, haga clic en el botón **Detener** para finalizar la sesión de depuración. Para asegurarse de que se recogen los nuevos cambios, no olvide reiniciar (detener y volver a ejecutar) la sesión de depuración.

    ![Detener la opción de depuración](media/azure-functions-lab-image22.png)

1. En el método **Run** método, reemplace las definiciones **x** e **y** con el código siguiente. Este código extrae los valores de la cadena de consulta de la dirección URL para que la operación de suma pueda realizarse dinámicamente en función de los parámetros proporcionados.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Ejecute la aplicación.

1. Vuelva a la ventana del explorador y anexe la cadena `/?x=2&y=3` a la dirección URL. Ahora, la dirección URL completa debería ser `http://localhost:7071/api/Add?x=2&y=3`. Vaya a la nueva dirección URL.

1. Esta vez el resultado debería reflejar los nuevos parámetros. No dude en ejecutar el proyecto con valores diferentes. Tenga en cuenta que no hay ninguna comprobación de errores, por lo que los parámetros no válidos o que faltan producirán un error.

1. Detenga la sesión de depuración.


## <a name="exercise-4-working-with-functionjson"></a>Ejercicio 4: Trabajar con function.json

1.  En el ejercicio anterior, se mencionó que "Visual Studio para Mac" generó una función de trabajo para la función de Azure definida en la biblioteca. Esto es porque Azure Functions realmente no usa los atributos del método en tiempo de ejecución, sino que usa una convención de sistema de archivos de tiempo de compilación para configurar dónde y cómo se ponen a disposición las funciones de Azure. En el **Panel de solución**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Mostrar en Finder**.

     ![Opción del menú Mostrar en Finder](media/azure-functions-lab-image23.png)

1. Navegue por el sistema de archivos hasta que llegue a **bin/Debug/netstandard2.0**. Debería haber una carpeta denominada **Add**. Esta carpeta se creó para que se corresponda con el atributo de nombre de la función en el código C#. Expanda la carpeta Add para mostrar un único archivo **function.json**. Este archivo se usa en tiempo de ejecución para hospedar y administrar la función de Azure. Para otros modelos de lenguaje sin compatibilidad con el tiempo de compilación (como el script de C# o JavaScript), estas carpetas deben crearse y mantenerse de forma manual. Para los desarrolladores de C#, se generan automáticamente desde los metadatos del atributo al compilar. Haga clic con el botón derecho sobre **function.json** y seleccione abrirlo en Visual Studio.

    ![function.json en el directorio de archivos](media/azure-functions-lab-image24.png)

1. Dados los anteriores pasos de este tutorial, debería tener un conocimiento básico de los atributos de C#. Teniendo esto en cuenta, este JSON debería resultarle familiar. Pero hay algunos elementos que no se recogen en los anteriores ejercicios. Por ejemplo, cada **enlace** debería tener su **dirección** establecida. Como puede deducir, **"en"** significa que el parámetro es de entrada, mientras que **"out"** indica que el parámetro es un valor devuelto (a través de **$return**) o un parámetro de **salida**  al método. También tendrá que especificar el **scriptFile** (relativo a su ubicación final) y el método **entryPoint** (público y estático) dentro del ensamblado. En los siguientes pasos agregará una ruta de acceso de la función personalizada con este método, así que copie el contenido de este archivo al portapapeles.

    ![archivo funtion.json abierto en Visual Studio para Mac](media/azure-functions-lab-image25.png)

1. En **Panel de solución**, haga clic con el botón derecho en el nodo de proyecto **AzureFunctionsLab** y seleccione **Agregar > Nueva carpeta**. Asigne el nombre **Adder** a la nueva carpeta. Por convención predeterminada, el nombre de esta carpeta definirá la ruta de acceso a la API, como **api/Adder**.

    ![Opción de nueva carpeta](media/azure-functions-lab-image26.png)

1. Haga clic con el botón derecho en la carpeta **Adder** y seleccione **Agregar > Nuevo archivo**.

    ![Opción de nuevo archivo](media/azure-functions-lab-image27.png)

1. Seleccione la categoría **Web** y la plantilla **Archivo JSON vacío**. Establezca el **Nombre** en **función** y haga clic en **Nuevo**.

    ![Opción de archivo JSON vacío](media/azure-functions-lab-image28.png)

1. Pegue el contenido del otro **function.json** (del paso 3) para reemplazar el contenido predeterminado del archivo recién creado.

1. Quite las siguientes líneas de la parte superior del archivo json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Al final del primer enlace, (después de la línea **"name": "req"**), agregue las propiedades siguientes: No olvide incluir una coma en la línea anterior. Esta propiedad sobrescribe la raíz predeterminada de tal forma que ahora extraerá los parámetros **int** de la ruta de acceso y los colocará en los parámetros del método denominados **x** e **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Agregue otro enlace debajo del primero. Este enlace administra el valor devuelto de la función. No olvide incluir una coma en la línea anterior:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Actualice también la propiedad **entryPoint** al final del archivo para que use un método denominado **"Add2"**, como se muestra a continuación. Con esto se muestra que la ruta de acceso **api/Adder...** podría asignarse a un método apropiado con cualquier nombre (aquí, **Add2**).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. El archivo **function.json** debería parecerse al json siguiente:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. El último paso necesario para hacer que todo esto funciones es ordenar a Visual Studio para Mac que copie este archivo a la misma ruta de acceso relativa en el directorio de salida cada vez que cambie. Con el archivo seleccionado, elija la ficha Propiedades a la derecha de la barra y, para **copiar en el directorio de salida** seleccione **Copiar si es posterior**:

    ![Opciones de propiedades para el archivo json](media/azure-functions-lab-image30.png)

1. En **Add.cs**, reemplace el método `Run` (incluido el atributo) con el método siguiente para que realice la función esperada. Es muy similar a `Run`, excepto en que no usa ningún atributo y tiene parámetros explícitos para **x** e **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```
1. Presione **F5** para compilar y ejecutar el proyecto.

1. Cuando finalice la compilación y la plataforma gire, indicará que hay una segunda ruta disponible para las solicitudes que se asigna para el método recién agregado:

    ![Dirección URL para las funciones Http](media/azure-functions-lab-image31.png)

1. Devuelva la ventana del explorador y vaya a **http://localhost:7071/api/Adder/3/5**.

1. Esta vez el método funciona una vez más, y extrae los parámetros de la ruta de acceso y genera una suma.

1. Vuelva a **Visual Studio para Mac** y termine la sesión de depuración.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Ejercicio 5: Trabajar con tablas de almacenamiento de Azure

A menudo, el servicio que compile podría ser mucho más complejo que lo que hemos creado hasta ahora y requerir una cantidad significativa de tiempo o infraestructura para ejecutarse. En este caso, podría resultarle efectivo aceptar las solicitudes que se ponen en cola para su procesamiento cuando los recursos estén disponibles, los cuales son compatibles con Azure. En otros casos tendrá que almacenar los datos de forma centralizada. Las tablas de Azure Storage permiten hacerlo rápidamente. 

1. Agregue la clase siguiente a **Add.cs**. Debe ir dentro del espacio de nombres, pero fuera de la clase existente.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. En la clase **Add**, agregue el siguiente código para introducir otra función. Tenga en cuenta que este es único hasta el momento, ya que no implica una respuesta HTTP. La última línea devuelve una nueva **TableRow** rellenada con alguna información clave que le resultará fácil de recuperar más adelante (**PartitionKey** y **RowKey**), así como sus parámetros y la suma. El código dentro del método también usa el **TraceWriter** para que le resulte más fácil saber cuándo se ejecuta la función.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");
    
        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```
1. Presione **F5** para compilar y ejecutar el proyecto.

1. En la pestaña del explorador, vaya a **http://localhost:7071/api/Process/4/6**. Esto colocará otro mensaje a la cola, cuyo resultado final será que se agrega otra fila a la tabla.

1. Vuelva a **Terminal** y espere a la solicitud entrante para **4 + 6**.

    ![Terminal de salida que muestra una solicitud de adición](media/azure-functions-lab-image32.png)

1. Vuelva al explorador para actualizar la solicitud a la misma dirección URL. Esta vez verá un error después del método **Process**. Esto es porque el código está intentando agregar una fila a la tabla de Azure Table Storage mediante una combinación de clave de partición y fila que ya existe.

    ``` 
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Finalice la sesión de depuración.

1. Para mitigar el error, agregue el parámetro siguiente a la definición del método inmediatamente antes del parámetro **TraceWriter**. Este parámetro ordena a la plataforma de Azure Functions que intente recuperar un **TableRow** desde la tabla **Resultados** en la **PartitionKey** que hemos utilizado para almacenar los resultados. Pero lo realmente mágico tiene lugar cuando se da cuenta de que la **RowKey** se genera dinámicamente en función de los parámetros **x** e **y** para el mismo método. Si esa fila ya existe, entonces **tableRow** la tendrá cuando el método comience sin que el desarrollador requiera ningún trabajo adicional. Si la fila no existe, entonces simplemente será null. Este tipo de eficacia permite que los desarrolladores se centren en la lógica de negocios importante y no en la infraestructura.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Agregue el código siguiente al principio del método. Si **tableRow** no es null, ya tendremos los resultados de la operación que se solicita y se puede devolver inmediatamente. En caso contrario, la función continúa como antes. Aunque esto puede no ser la manera más sólida de devolver los datos, muestra que puede coordinar operaciones extremadamente complejas en múltiples niveles escalables con muy poco código.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Presione **F5** para compilar y ejecutar el proyecto.

1. En la pestaña del explorador, actualice la dirección URL a **http://localhost:7071/api/Process/4/6**. Puesto que la fila de tabla para este registro existe, debería devolver inmediatamente y sin errores. Puesto que no hay ninguna salida HTTP, puede ver el resultado en Terminal.

    ![Terminal de salida que muestra que la fila de la tabla ya existe](media/azure-functions-lab-image33.png)

1. Actualice la dirección URL para reflejar una combinación que todavía no ha probado, como **http://localhost:7071/api/Process/5/7**. Tenga en cuenta el mensaje en Terminal, que indica que no se encontró la fila de tabla (como se esperaba).

    ![Terminal de salida que muestra nuevo proceso](media/azure-functions-lab-image34.png)

1. Vuelva a **Visual Studio para Mac** y termine la sesión de depuración.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON. 

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Resumen

En esta práctica ha aprendido a empezar a compilar Azure Functions con Visual Studio para Mac.

