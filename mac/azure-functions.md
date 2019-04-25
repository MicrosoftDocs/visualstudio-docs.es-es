---
title: Introducción a Azure Functions
description: Uso de Azure Functions en Visual Studio para Mac.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: ac0786e9b52a149fe8067c41aaabe61ad9fd5c87
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857248"
---
# <a name="introduction-to-azure-functions"></a>Introducción a Azure Functions

Azure Functions es una manera de crear y ejecutar fragmentos de código orientados a eventos (funciones) en la nube, sin tener que proporcionar o administrar explícitamente la infraestructura. Para obtener más información sobre Azure Functions, consulte [Documentación de Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Requisitos

Las herramientas de Azure Functions se incluyen en **Visual Studio para Mac 7.5** y versiones posteriores.

Para crear e implementar funciones también necesita una suscripción de Azure, que está disponible de forma gratuita en [https://azure.com/free](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Crear su primer proyecto de Azure Functions

1. En Visual Studio para Mac, seleccione **Archivo > Nueva solución**.
2. En el cuadro de diálogo Nuevo proyecto, seleccione la plantilla de Azure Functions en **Nube > General** y haga clic en **Siguiente**:

    ![Cuadro de diálogo de Nuevo proyecto con la opción de Azure Functions](media/azure-functions-image1.png)

3. Seleccione la plantilla inicial de Azure Functions que quiera usar, escriba el nombre de función y haga clic en **Siguiente**.

    ![Cuadro de diálogo Nuevo proyecto con las plantillas de Azure Functions](media/azure-functions-image2.png)

    > [!TIP]
    > Aunque el tiempo de ejecución y las plantillas (CLI) de Azure Functions se mantienen lo más actualizados posible, inevitablemente se quedan obsoletos. Al crear un proyecto de Functions, Visual Studio para Mac comprobará las actualizaciones de la CLI y le notificará tal y como se muestra en la imagen siguiente. Basta con hacer clic en el botón para descargar las plantillas actualizadas.
    > ![Cuadro de diálogo Nuevo proyecto con las actualizaciones de Azure Functions disponibles](media/azure-functions-update.png)

    Según el tipo de función que seleccione, la siguiente página le solicitará que especifique los detalles, como los derechos de acceso, como se muestra en la siguiente imagen:

    ![Cuadro de diálogo Nuevo proyecto con la opción adicional](media/azure-functions-image3.png)

    Para más información sobre los distintos tipos de plantillas de Azure Functions y las propiedades de enlace necesarias para configurar cada plantilla, vea la sección [Plantillas de función disponibles](#available-function-templates). Para este ejemplo, se usa un desencadenador Http con acceso de derechos establecidos en anónimos.

4. Una vez que haya definido los parámetros, elija la ubicación para el proyecto y haga clic en **Crear**.

Visual Studio para Mac crea un proyecto de .NET Standard con una función predeterminada incluida. También incluye referencias de NuGet para una variedad de paquetes de **AzureWebJobs**, así como el paquete **Newtonsoft.Json**.

![Editor de Visual Studio para Mac que muestra una nueva función Azure desde la plantilla](media/azure-functions-newproj.png)

El nuevo proyecto contiene los siguientes archivos:

* **your-function-name.cs**: esta clase contiene código reutilizable para la función que ha seleccionado. Contiene un atributo **FunctionName** con el nombre de la función y un atributo desencadenador que especifica lo que desencadena la función (por ejemplo, una solicitud HTTP). Para obtener más información sobre el método de funciones, consulte el artículo [Referencia para desarrolladores de C# de Azure Functions](/azure/azure-functions/functions-dotnet-class-library).
* **host.json**: este archivo describe las opciones de configuración global para el host de Functions. Para un archivo de ejemplo e información sobre la configuración disponible para este archivo, consulte la [Referencia de host.json para Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.json**: este archivo contiene toda la configuración para ejecutar las funciones de forma local. Esta configuración se utiliza con las herramientas principales de Azure Functions. Para obtener más información, consulte [Archivo de configuración local](/azure/azure-functions/functions-run-local#local-settings-file) en el artículo de las herramientas principales de Azure Functions.

Ahora que ha creado un nuevo proyecto de Azure Functions en Visual Studio para Mac, puede probar la función desencadenada HTTP predeterminada desde el equipo local.

## <a name="testing-the-function-locally"></a>Probar la función localmente

Con compatibilidad con Azure Functions en Visual Studio para Mac puede probar y depurar la función en el equipo de desarrollo local.

1. Para probar la función localmente, presione el botón **Ejecutar** en Visual Studio para Mac:

    ![Botón Iniciar la depuración en Visual Studio para Mac](media/azure-functions-run.png)

1. Al ejecutar el proyecto se inicia la depuración local en Azure Functions y se abre una nueva ventana de Terminal, como se muestra en la siguiente imagen:

    ![ventana de terminal que muestra la salida de la función](media/azure-functions-terminal.png)

    Copie la dirección URL de la salida.

3. Pegue la dirección URL de la solicitud HTTP en la barra de direcciones del explorador. Agregue la cadena de consulta `?name=<yourname>` al final de la dirección URL y ejecute la solicitud. La siguiente imagen muestra la respuesta en el explorador para la solicitud GET local devuelta por la función:

    ![solicitud HTTP en el explorador](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Agregar otra función al proyecto

Las plantillas de función permiten crear rápidamente nuevas funciones mediante los desencadenadores y las plantillas más comunes. Para crear otro tipo de función, haga lo siguiente:

1. Para agregar una nueva función, haga doble clic en el nombre del proyecto y seleccione **Agregar > Agregar función...**:

    ![acción contextual para agregar una nueva función](media/azure-functions-addnew.png)

2. Desde el cuadro de diálogo **Nueva función de Azure**, seleccione la función que necesita:

    ![cuadro de diálogo de nueva función de Azure](media/azure-functions-image4.png)

    En la sección [Plantillas de función disponibles](#available-function-templates) se proporciona una lista de las plantillas Azure Function.

Puede usar el procedimiento anterior para agregar más funciones a su proyecto de Function App. Cada función del proyecto puede tener un desencadenador diferente, pero una función debe tener exactamente un desencadenador. Para más información, vea [Conceptos básicos sobre los enlaces y desencadenadores de Azure Functions](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publicar en Azure

1. Haga clic con el botón derecho en el nombre del proyecto y seleccione **Publicar > Publicar en Azure** :  ![Opción de menú Publicar en Azure](media/azure-functions-image5.png)
2. Si ya ha conectado su cuenta de Azure para Visual Studio para Mac, se mostrará una lista de servicios de aplicaciones disponibles. Si aún no ha iniciado sesión, se le pedirá que lo haga.
3. En el cuadro de diálogo **Publicar en Azure App Service**, puede seleccionar un servicio de aplicación existente o crear uno nuevo haciendo clic en **Nuevo**.
4. En el cuadro de diálogo **Crear instancia de App Service**, especifique la configuración:  ![Opción de menú Publicar en Azure](media/azure-functions-image7.png)

    |Parámetro  |Descripción  |
    |---------|---------|
    |**Nombre de App Service**|Un nombre único global que identifica la nueva instancia de Function App.|
    |**Suscripción**|La suscripción de Azure que se va a usar.|
    |**[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)**|Nombre del grupo de recursos en el que se va a crear la instancia de Function App. Elija **+** para crear un nuevo grupo de recursos.|
    |**[Plan de servicio](/azure/azure-functions/functions-scale)**|Elija un plan existente o cree un plan personalizado. Elija una ubicación en una región cerca de usted o cerca de otros servicios a los que acceda la función.|

5. Haga clic en **Siguiente** para crear una cuenta de almacenamiento. El runtime de Functions necesita una cuenta de almacenamiento de Azure. Haga clic en **Personalizado** para crear una cuenta de almacenamiento de propósito general o usar una existente:

    ![Opción de menú Publicar en Azure](media/azure-functions-image8.png)

6. Haga clic en **Crear** para crear una instancia de Function App y los recursos relacionados en Azure con esta configuración e implementar el código del proyecto de función.

7. Puede que se muestre un cuadro de diálogo durante la publicación que indique "Actualizar versión de Functions en Azure". Haga clic en **Sí**:

    ![Opción de menú Publicar en Azure](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Configuración de Function App

Cualquier configuración que agregue en local.settings.json debe agregarse también a Function App en Azure. Esta configuración no se carga automáticamente cuando se publica el proyecto.

Para Tener acceso a la configuración de la aplicación, vaya a Azure Portal en [https://ms.portal.azure.com/](https://ms.portal.azure.com/). En **Instancias de Function App**, seleccione **Instancias de Function App** y resalte el nombre de función:

![menú Azure Functions](media/azure-functions-image9.png)

En la pestaña **Información general**, seleccione **Configuración de la aplicación** en **Características configuradas**:

![Pestaña Información general de Azure Function](media/azure-functions-image10.png)

Desde aquí se puede establecer la configuración de la aplicación para Function App, donde puede agregar la nueva configuración de la aplicación o modificar las existentes:

![área de configuración de aplicación de Azure Portal](media/azure-functions-image11.png)

Hay un valor importante que es posible que tenga que configurar: `FUNCTIONS_EXTENSION_VERSION`. Al publicar desde Visual Studio para Mac, este valor debe establecerse en **beta**.

## <a name="available-function-templates"></a>Plantillas de función disponibles

- **Desencadenador de GitHub**: responder a los eventos que se producen en los repositorios de GitHub. Para obtener más información, vea la página [Creación de una función desencadenada por Webhook de GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Autor del comentario de GitHub: esta función se ejecutará cuando reciba un webhook de GitHub para un problema o solicitud de incorporación de cambios y agregue un comentario.
    - WebHook de GitHub: esta función se ejecutará cuando reciba un WebHook de GitHub.

- **HTTP**: desencadena la ejecución del código mediante una solicitud HTTP. Hay plantillas explícitas para los siguientes desencadenadores HTTP:
    - Desencadenador HTTP
    - Http GET CRUD
    - Http POST CRUD
    - Desencadenador HTTP con parámetros


- **Temporizador**: ejecutar una limpieza u otras tareas de lote en una programación predefinida. Esta plantilla tiene dos campos: un nombre y una programación, que es una expresión de CRON de seis campos. Para obtener más información, vea la página [Cree una función en Azure que se desencadena mediante un temporizador](/azure/azure-functions/functions-create-scheduled-function)


- **Desencadenador de cola**: se trata de una función que responderá a los mensajes a medida que llegan a la cola de Azure Storage. Además del nombre de la función, esta plantilla toma una **ruta de acceso** (el nombre de la cola desde la que se leerá el mensaje) y una cuenta de almacenamiento **Conexión** (el nombre de la configuración de la aplicación que contiene la cadena de conexión de la cuenta de almacenamiento). Para obtener más información, vea la página [Crear una función desencadenada por Azure Queue Storage](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Desencadenador de blob**: procesa blobs de Azure Storage cuando se agregan a un contenedor. Además del nombre de función, esta plantilla también tiene una propiedad de ruta de acceso y de conexión. La propiedad de ruta de acceso es la ruta de acceso dentro de la cuenta de almacenamiento que el desencadenador supervisará. La cuenta de conexión es el nombre de la configuración de aplicación que contiene la cadena de conexión de la cuenta de almacenamiento. Para obtener más información, vea la página [Crear una función desencadenada por Azure Blob Storage](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **WebHook genérico**: se trata de una función sencilla que se ejecutará cada vez que recibe una solicitud de servicio que admita webhooks. Para más información, vea [Creación de una función desencadenada mediante un webhook genérico](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Orquestación Durable Functions**: Durable Functions le permite escribir funciones con estado en un entorno sin servidor. La extensión administra el estado, los puntos de control y los reinicios en su nombre. Para más información, vea las guías de Azure Functions en [Durable Functions](/azure/azure-functions/durable-functions-overview).

- **Redimensionador de imagen**: esta función crea imágenes redimensionadas cada vez que un blob se agrega a un contenedor. La plantilla toma la cadena de conexión y la ruta de acceso para el desencadenador, una salida de imagen pequeña y una salida de imagen media.

- **Token de SAS**: esta función genera un token de SAS para un contenedor y nombre de blob de Azure Storage determinados. Además del nombre de función, esta plantilla también tiene una propiedad de ruta de acceso y de conexión. La propiedad de ruta de acceso es la ruta de acceso dentro de la cuenta de almacenamiento que el desencadenador supervisará. La cuenta de conexión es el nombre de la configuración de aplicación que contiene la cadena de conexión de la cuenta de almacenamiento. También se deben establecer los **derechos de acceso**. El nivel de autorización controla si la función requiere una clave de API y qué clave utilizar; Función usa una tecla de función; Administrador usa la clave maestra. Para obtener más información, vea el ejemplo [C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) (Función de Azure de C# para generar tokens de SAS).
