---
title: Publicar una aplicación de Node.js en App Service de Linux
description: Puede publicar aplicaciones de Node.js creadas en Visual Studio en App Service de Linux en Azure
ms.date: 11/1/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 20df5476a2ca6cf8fb0ffbf22e8106e51d17128d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58070313"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publicar una aplicación de Node.js en Azure (App Service de Linux)

Este tutorial le guía a lo largo de la tarea de crear una aplicación sencilla de Node.js y publicarla en Azure.

Al publicar una aplicación de Node.js en Azure, hay varias opciones. Estas incluyen Azure App Service, una máquina virtual con un sistema operativo de su elección, Azure Container Service (AKS) para la administración con Kubernetes, una instancia de contenedor con Docker, etc. Para obtener más detalles sobre cada una de estas opciones, vea [Compute](https://azure.microsoft.com/product-categories/compute/).

En este tutorial, la aplicación se implementa en [App Service de Linux](/azure/app-service/containers/app-service-linux-intro).
App Service de Linux implementa un contenedor Docker de Linux para ejecutar la aplicación de Node.js (a diferencia de App Service de Windows, que ejecuta aplicaciones de Node.js detrás de IIS en Windows).

En este tutorial se muestra cómo crear una aplicación de Node.js a partir de una plantilla instalada con Herramientas de Node.js para Visual Studio, insertar el código en un repositorio de GitHub y luego aprovisionar una instancia de Azure App Service a través del portal web de Azure para poder implementar desde el repositorio de GitHub. Para usar la línea de comandos para aprovisionar la instancia de Azure App Service e insertar el código desde un repositorio de Git local, vea [Creación de una aplicación web de Node.js](/azure/app-service/containers/quickstart-nodejs).

En este tutorial aprenderá a:
> [!div class="checklist"]
> * Crear un proyecto de Node.js
> * Crear un repositorio de GitHub para el código
> * Crear una instancia de App Service de Linux en Azure
> * Implementar en Linux

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la carga de trabajo de desarrollo de Node.js. 

    ::: moniker range=">=vs-2019"
    Si todavía no ha instalado Visual Studio 2019, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si todavía no ha instalado Visual Studio 2017, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
    ::: moniker-end

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

    ![Carga de trabajo Node.js en el instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Debe tener instalado el runtime de Node.js.

    Si todavía no lo tiene instalado, instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/). En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta un runtime instalado, puede configurar el proyecto para que haga referencia al runtime instalado en la página de propiedades (después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Crear un proyecto de Node.js para ejecutarlo en Azure

1. Abra Visual Studio.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. Cree una aplicación de Express de TypeScript.

    ::: moniker range=">=vs-2019"
    En el cuadro de diálogo **Crear un nuevo proyecto**, escriba **javascript** en el cuadro de búsqueda para filtrar los resultados, elija **Aplicación básica de Azure Node.js Express 4** y seleccione **Siguiente**. Luego, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y después seleccione **Node.js**. En el panel central, elija **Aplicación básica de Azure Node.js Express 4** y después haga clic en **Aceptar**.

    ![Creación de una aplicación de Express de TypeScript](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación básica de Azure Node.js Express 4**, debe agregar la carga de trabajo **Desarrollo de Node.js**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

    Visual Studio crea el proyecto y lo abre en el Explorador de soluciones (panel derecho).

1. Presione **F5** para compilar y ejecutar la aplicación y asegúrese de que todo funciona según lo previsto.

1. Seleccione **Archivo** > **Agregar al control de código fuente** para crear un repositorio de Git local para el proyecto.

    En este punto, hay una aplicación de Node.js que usa el marco de Express y está escrita en TypeScript funcionando y se inserta en el repositorio en el control de código fuente local.

1. Edite el proyecto como quiera antes de continuar con los pasos siguientes.

## <a name="push-code-from-visual-studio-to-github"></a>Insertar código de Visual Studio en GitHub

Para configurar GitHub para Visual Studio:

1. Asegúrese de que la [Extensión de GitHub para Visual Studio](https://visualstudio.github.com/) esté instalada y habilitada mediante el elemento de menú **Herramientas** > **Extensiones y actualizaciones**.

2. En el menú, seleccione **Ver** > **Otras ventanas** > **GitHub**.

    Se abre la ventana de GitHub.

3. Si no ve el botón **Comenzar** en la ventana de GitHub, haga clic en **Archivo** > **Agregar al control de código fuente** y espere a que la interfaz de usuario se actualice.

    ![Apertura de la ventana de GitHub](../javascript/media/azure-github-get-started.png)

4. Haga clic en **Comenzar**.

    Si ya está conectado a GitHub, aparece un cuadro de herramientas similar a la siguiente ilustración.

    ![Configuración del repositorio de GitHub](../javascript/media/azure-github-publish.png)

5. Rellene los campos del nuevo repositorio que se va a publicar y luego haga clic en **Publicar**.

    Transcurridos unos instantes, aparece un banner que indica "Repositorio creado correctamente".

    En la siguiente sección se obtiene información sobre cómo publicar desde este repositorio en Azure App Service en Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Crear una instancia de App Service de Linux en Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Seleccione **App Services** en la lista de servicios de la izquierda y luego haga clic en **Agregar**.

3. En caso necesario, cree un grupo de recursos y un plan de App Service para hospedar la nueva aplicación.

4. Asegúrese de establecer el **SO** en **Linux** y **Pila en tiempo de ejecución** en la versión necesaria de Node.js, como se muestra en la ilustración.

    ![Creación de una instancia de App Service de Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Haga clic en **Crear** para crear la instancia de App Service.

    Puede tardar unos minutos en implementarse.

6. Una vez implementada, vaya a la sección **Configuración de la aplicación** y agregue un valor con el nombre `SCM_SCRIPT_GENERATOR_ARGS` y un valor de `--node`.

    ![Configuración de la aplicación](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > El proceso de implementación de App Service usa un conjunto de técnicas heurísticas para determinar qué tipo de aplicación se va a probar y ejecutar. Si se detecta un archivo .*sln* en el contenido distribuido, asume que se va a implementar un proyecto basado en MSBuild. El valor agregado arriba reemplaza esta lógica y especifica explícitamente que se trata de una aplicación de Node.js. Sin este valor, la aplicación de Node.js no se implementa si el archivo .*sln* forma parte del repositorio que se va a implementar en App Service.

7. Una vez implementada, abra la instancia de App Service y seleccione **Opciones de implementación**.

    ![Opciones de implementación](../javascript/media/azure-deployment-options.png)

8. Haga clic en **Elegir origen**, elija **GitHub** y luego configure los permisos necesarios.

    ![Permisos de GitHub](../javascript/media/azure-choose-source.png)

9. Seleccione el repositorio y la rama que se van a publicar y, luego, haga clic en **Aceptar**.

    ![Publicación en App Service de Linux](../javascript/media/azure-repo-and-branch.png)

    La página **Opciones de implementación** aparece durante la sincronización.

    ![Implementación y sincronización con GitHub](../javascript/media/azure-deployment-options-sync.png)

    Una vez finalizada la sincronización, aparece una marca de verificación.

    El sitio ya está ejecutando la aplicación de Node.js desde el repositorio de GitHub y es accesible en la dirección URL creada para Azure App Service (de forma predeterminada, el nombre asignado a Azure App Service seguido de ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modificar la aplicación e insertar cambios

1. Agregue el código que se muestra aquí a *app.ts* después de la línea `app.use('/users', users);`. Esto agrega una API REST en la dirección URL */api*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Compile el código y pruébelo en local, luego insértelo en el repositorio de GitHub.

    En Azure Portal se tarda unos segundos en detectar los cambios en el repositorio de GitHub; luego se inicia una nueva sincronización de la implementación. El resultado es similar a la ilustración siguiente.

    ![Modificación y sincronización](../javascript/media/azure-changes-detected.png)

3. Una vez completada la implementación, vaya al sitio público y anexe */api* a la dirección URL. Se devuelve la respuesta JSON.

## <a name="troubleshooting"></a>Solución de problemas

* Si se produce un problema en el proceso de node.exe (es decir, se produce una excepción no controlada), el contenedor se reinicia.
* Cuando se reinicia el contenedor, se ejecuta por medio de diferentes técnicas heurísticas para determinar cómo iniciar el proceso de Node.js. Los detalles de la implementación pueden verse en [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Puede conectarse al contenedor en ejecución a través de SSH para investigar. Esto se hace fácilmente con Azure Portal. Seleccione la instancia de App Service y desplácese hacia abajo en la lista de herramientas hasta alcanzar **SSH** en la sección **Herramientas de desarrollo**.
* Para ayudar a solucionar problemas, vaya a la opción **Registros de diagnóstico** de App Service y cambie la opción **Registro de contenedor de Docker** de **Desactivado** a **Sistema de archivos**. Los registros se crean en el contenedor en */home/LogFiles/*_docker.log* y se puede acceder a ellos en el cuadro mediante SSH o FTP (S).
* Puede asignar un nombre de dominio personalizado al sitio, en lugar de la dirección URL *.azurewebsites.net asignada de forma predeterminada. Para obtener más detalles, vea el tema [Asignación de un dominio personalizado](/azure/app-service/app-service-web-tutorial-custom-domain).
* Se recomienda implementar en un sitio de ensayo para realizar más pruebas antes de pasar a producción. Para obtener detalles sobre cómo configurarlo, vea el tema [Creación de entornos de ensayo](/azure/app-service/web-sites-staged-publishing).
* Vea [Preguntas más frecuentes sobre Azure App Service en Linux](/azure/app-service/containers/app-service-linux-faq) para leer las preguntas más frecuentes.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial ha aprendido a crear una instancia de App Service de Linux y a implementar una aplicación de Node.js en el servicio. Es posible que quiera obtener más información sobre App Service de Linux.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)
