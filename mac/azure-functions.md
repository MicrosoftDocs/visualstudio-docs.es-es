---
title: Introducción a Azure Functions
description: Uso de Azure Functions en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870416"
---
# <a name="introduction-to-azure-functions"></a>Introducción a Azure Functions

Azure Functions es una manera de crear y ejecutar fragmentos de código orientados a eventos (funciones) en la nube, sin tener que proporcionar o administrar explícitamente la infraestructura. Para obtener más información sobre Azure Functions, consulte [Documentación de Azure Functions](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Requisitos

Las herramientas de Azure Functions se incluyen en **Visual Studio para Mac 7.5**.

Para crear e implementar funciones también necesita una suscripción de Azure, que está disponible de forma gratuita en [https://azure.com/free](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Crear su primer proyecto de Azure Functions

1. En Visual Studio para Mac, seleccione **Archivo > Nueva solución...** 
2. En el cuadro de diálogo Nuevo proyecto, seleccione la plantilla de Azure Functions en **Nube > General** y haga clic en **Siguiente**:

    ![Cuadro de diálogo de Nuevo proyecto con la opción de Azure Functions](media/azure-functions-image1.png)

3. Escriba un **nombre de proyecto** y seleccione **Crear**.

Visual Studio para Mac crea un proyecto estándar de .NET con una función de HttpTrigger predeterminada incluida. También incluye referencias de NuGet para una variedad de paquetes de **AzureWebJobs**, así como el paquete **Newtonsoft.Json**.

![Editor de Visual Studio para Mac que muestra una nueva función Azure desde la plantilla](media/azure-functions-newproj.png)

El nuevo proyecto contiene los siguientes archivos:

* **HttpTrigger.cs**: esta clase contiene código reutilizable para una función desencadenada por HTTP. Contiene un atributo **FunctionName** con el nombre de la función y un atributo desencadenador, **HttpTrigger**, que especifica que la función se desencadena por una solicitud HTTP. Para obtener más información sobre el método de funciones, consulte el artículo [Referencia para desarrolladores de C# de Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library).
* **host.json**: este archivo describe las opciones de configuración global para el host de Functions. Para un archivo de ejemplo e información sobre la configuración disponible para este archivo, consulte la [Referencia de host.json para Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **local.settings.json**: este archivo contiene toda la configuración para ejecutar las funciones de forma local. Esta configuración se utiliza con las herramientas principales de Azure Functions. Para obtener más información, consulte [Archivo de configuración local](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) en el artículo de las herramientas principales de Azure Functions.

Ahora que ha creado un nuevo proyecto de Azure Functions en Visual Studio para Mac, puede probar la función desencadenada HTTP predeterminada desde el equipo local.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Probar la función localmente

Con compatibilidad con Azure Functions en Visual Studio para Mac puede probar y depurar la función en el equipo de desarrollo local.

1. Para probar la función localmente, presione el botón **Ejecutar** en Visual Studio para Mac:

    ![Botón Iniciar la depuración en Visual Studio para Mac](media/azure-functions-run.png)

1. Al ejecutar el proyecto se inicia la depuración local en Azure Functions y se abre una nueva ventana de Terminal, como se muestra en la siguiente imagen: 

    ![ventana de terminal que muestra la salida de la función](media/azure-functions-terminal.png) 

    Copie la dirección URL de la salida.

3. Pegue la dirección URL de la solicitud HTTP en la barra de direcciones del explorador. Agregue la cadena de consulta `?name=<yourname>` al final de la dirección URL y ejecute la solicitud. La siguiente imagen muestra la respuesta en el explorador para la solicitud GET local devuelta por la función:

    ![solicitud HTTP en el explorador](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Crear una nueva función

Las plantillas de función permiten crear rápidamente nuevas funciones mediante los desencadenadores y las plantillas más comunes. Cuando se crea un nuevo proyecto de Azure Functions, se incluye automáticamente una función HttpTrigger. Para crear otro tipo de función, haga lo siguiente:

1. Quite el archivo **HttpTrigger.cs** haciendo clic con el botón derecho sobre él y seleccione **Quitar**. En la siguiente alerta, seleccione **Eliminar** para quitarlo de su proyecto:

    ![cuadro de diálogo para quitar el archivo del proyecto](media/azure-functions-remove.png)

2. Para agregar una nueva función, haga doble clic en el nombre del proyecto y seleccione **Agregar > Agregar función...**:

    ![acción contextual para agregar una nueva función](media/azure-functions-addnew.png)

3. Desde el cuadro de diálogo **Nueva función de Azure**, seleccione la función que necesita:

    ![cuadro de diálogo de nueva función de Azure](media/azure-functions-newfunction.png)

    En la sección siguiente se proporciona una lista de las plantillas de funciones de Azure.

## <a name="available-function-templates"></a>Plantillas de función disponibles

- **HTTP**: desencadena la ejecución del código mediante una solicitud HTTP. Hay plantillas explícitas para los siguientes desencadenadores HTTP:
    - Http GET CRUD
    - Http POST CRUD
    - Desencadenador HTTP con parámetros
    - Desencadenador HTTP
- **Temporizador**: ejecutar una limpieza u otras tareas de lote en una programación predefinida. Esta plantilla tiene dos campos: un nombre y una programación, que es una expresión de CRON de seis campos. Para obtener más información, vea la página [Cree una función en Azure que se desencadena mediante un temporizador](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)
- **Desencadenador de GitHub**: responder a los eventos que se producen en los repositorios de GitHub. Para obtener más información, vea la página [Creación de una función desencadenada por Webhook de GitHub](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Autor del comentario de GitHub: esta función se ejecutará cuando reciba un webhook de GitHub para un problema o solicitud de incorporación de cambios y agregue un comentario.
    - WebHook de GitHub: esta función se ejecutará cuando recibe un WebHook de GitHub
- **Desencadenador de blob**: procesa blobs de Azure Storage cuando se agregan a un contenedor. Además del nombre de función, esta plantilla también tiene una propiedad de ruta de acceso y de conexión. La propiedad de ruta de acceso es la ruta de acceso dentro de la cuenta de almacenamiento que el desencadenador supervisará. La cuenta de conexión es el nombre de la configuración de aplicación que contiene la cadena de conexión de la cuenta de almacenamiento. Para obtener más información, vea la página [Crear una función desencadenada por Azure Blob Storage](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Desencadenador de cola**: se trata de una función que responderá a los mensajes a medida que llegan a la cola de Azure Storage. Además del nombre de la función, esta plantilla toma una **ruta de acceso** (el nombre de la cola desde la que se leerá el mensaje) y una cuenta de almacenamiento **Conexión** (el nombre de la configuración de la aplicación que contiene la cadena de conexión de la cuenta de almacenamiento). Para obtener más información, vea la página [Crear una función desencadenada por Azure Queue Storage](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **WebHook genérico**: se trata de una función sencilla que se ejecutará cada vez que recibe una solicitud de servicio que admita webhooks. Para obtener más información, vea la página [Creación de una función desencadenada por un webhook genérico](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function)
- **Redimensionador de imagen**: esta función crea imágenes redimensionadas cada vez que un blob se agrega a un contenedor. La plantilla toma la cadena de conexión y la ruta de acceso para el desencadenador, una salida de imagen pequeña y una salida de imagen media.
- **Token de SAS**: esta función genera un token de SAS para un contenedor y nombre de blob de Azure Storage determinados. Además del nombre de función, esta plantilla también tiene una propiedad de ruta de acceso y de conexión. La propiedad de ruta de acceso es la ruta de acceso dentro de la cuenta de almacenamiento que el desencadenador supervisará. La cuenta de conexión es el nombre de la configuración de aplicación que contiene la cadena de conexión de la cuenta de almacenamiento. También se deben establecer los **derechos de acceso**. El nivel de autorización controla si la función requiere una clave de API y qué clave utilizar; Función usa una tecla de función; Administrador usa la clave maestra. Para obtener más información, vea el ejemplo [C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) (Función de Azure de C# para generar tokens de SAS).
- **Orquestación Durable Functions**: Durable Functions le permite escribir funciones con estado en un entorno sin servidor. La extensión administra el estado, los puntos de control y los reinicios en su nombre. Para obtener más información, vea las guías de Azure Functions en [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)