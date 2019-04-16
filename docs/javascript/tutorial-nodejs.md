---
title: Creación de una aplicación Node.js y Express
description: En este tutorial, creará una aplicación con Node.js Tools para Visual Studio.
ms.date: 09/24/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ebc255e41e8e73739f83e69ab120f397cc46f49c
ms.sourcegitcommit: 05d104a14ff357d599ff274f97cd59d464ee4a46
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2019
ms.locfileid: "58897717"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Tutorial: Crear una aplicación Node.js y Express en Visual Studio

En este tutorial para el desarrollo de Visual Studio con Node.js y Express, se crea una sencilla aplicación web de Node.js, agregará código, explorará algunas características del IDE y ejecutará la aplicación. Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

En este tutorial aprenderá a:
> [!div class="checklist"]
> * Crear un proyecto de Node.js
> * Agregar algo de código
> * Usar IntelliSense para editar código
> * Ejecutar la aplicación
> * Alcanzar un punto de interrupción en el depurador

## <a name="before-you-begin"></a>Antes de empezar

Esta es una sección rápida de P+F para presentar algunos conceptos clave.

### <a name="what-is-nodejs"></a>¿Qué es Node.js?

Node.js es un entorno de runtime de JavaScript para servidor que ejecuta JavaScript en el servidor.

### <a name="what-is-npm"></a>¿Qué es npm?

npm es el administrador de paquetes predeterminado de Node.js. El administrador de paquetes permite a los programadores publicar y compartir más fácilmente el código fuente de las bibliotecas de Node.js, y está diseñado para simplificar la instalación, la actualización y la desinstalación de bibliotecas.

### <a name="what-is-express"></a>¿Qué es express?

Express es un marco de aplicación web que sirve de marco de trabajo de servidor para Node.js en la compilación de aplicaciones web. Express le permite elegir diferentes marcos de front-end para crear una interfaz de usuario, como Pug (anteriormente Jade). En este tutorial se usa Pug.

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

    Este tutorial se ha probado con Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Crear un proyecto de Node.js

Visual Studio administra los archivos de una aplicación en un *proyecto*. El proyecto incluye código fuente, recursos y archivos de configuración.

En este tutorial, empezará con un proyecto simple que contiene el código de una aplicación express y Node.js.

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **Node.js**, elija **Create a new Basic Azure Node.js Express 4 application** (Crear una aplicación básica de Azure Node.js Express 4) (JavaScript). En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y elija **Node.js**. En el panel central, elija **Aplicación básica de Azure Node.js Express 4** y después haga clic en **Aceptar**.
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación básica de Azure Node.js Express 4**, debe agregar la carga de trabajo **Desarrollo de Node.js**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

    Visual Studio crea la solución y abre el proyecto en el panel derecho. El archivo de proyecto *app.js* se abre en el editor (panel de la izquierda).

    ![Estructura del proyecto](../javascript/media/tutorial-project-structure.png)

    (1) El proyecto está resaltado en **negrita**. Tiene el nombre que le asignó en el cuadro de diálogo **Nuevo proyecto**. En el sistema de archivos, este proyecto se representa mediante un archivo *.njsproj* en la carpeta del proyecto. Para establecer propiedades y variables de entorno asociadas al proyecto, haga clic con el botón derecho en el proyecto y elija **Propiedades**. Puede hacer recorridos de ida y vuelta con otras herramientas de desarrollo, dado que el archivo de proyecto no realiza cambios personalizados en el origen del proyecto Node.js.

    (2) En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo *.sln* en el disco, es un contenedor para uno o más proyectos relacionados.

    (3) En el nodo npm se muestran todos los paquetes npm instalados. Puede hacer clic con el botón derecho en el nodo de npm para buscar e instalar paquetes de npm mediante un cuadro de diálogo, o instalar y actualizar los paquetes con la configuración de *package.json* y con las opciones que aparecen al hacer clic con el botón derecho en el nodo de npm.

    (4) *package.json* es un archivo usado por npm para administrar las dependencias y las versiones de los paquetes instalados localmente. Para obtener más información sobre este archivo, consulte [package.json configuration](../javascript/configure-packages-with-package-json.md) (Configuración de package.json).

    (5) Los archivos de proyecto como *app.js* se muestran en el nodo del proyecto. *app.js* es el archivo de inicio del proyecto, por lo que aparece en **negrita**. Puede establecer el archivo de inicio si hace clic con el botón derecho en un archivo del proyecto y selecciona **Establecer como archivo de inicio de Node.js**.

1. Abra el nodo **npm** y asegúrese de que todos los paquetes de npm necesarios están presentes.

    Si falta alguno (icono de signo de exclamación), haga clic con el botón derecho en el nodo **npm** y elija **Instalar los paquetes de NPM que faltan**.

## <a name="add-some-code"></a>Agregar algo de código

La aplicación utiliza Pug para el marco de trabajo front-end de JavaScript. Pug usa el código de marcado simple que se compila en HTML. (Pug está establecido como motor de visualización en *app.js*. El código que establece el motor de visualización en *app.js* es `app.set('view engine', 'pug');`).

1. En el Explorador de soluciones (panel de la derecha), abra la carpeta views y después *index.pug*.

1. Reemplace el contenido por el marcado siguiente.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    El código anterior se usa para generar dinámicamente una página HTML con un título y un mensaje de bienvenida. La página incluye también código que muestra una imagen que cambia cada vez que se presiona un botón.

1. En la carpeta routes, abra *index.js*.

1. Agregue el código siguiente antes de llamar a `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Este código crea un objeto de datos que se pasa a la página HTML generada dinámicamente.

1. Reemplace la función `router.get` por el código siguiente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    El código anterior establece la página actual con el objeto de enrutador de Express y presenta la página, que pasará el objeto de datos y el título a la página. El archivo *index.pug* se especifica aquí como la página que se va a cargar cuando se ejecute *index.js*. *index.js* está configurado como la ruta predeterminada en el código de *app.js* (no mostrado).

    Para realizar la demostración de varias características de Visual Studio, se incluye un error en la línea de código que contiene `res.render`. Debe corregir el error para que se pueda ejecutar la aplicación. Puede hacerlo en la sección siguiente.

## <a name="use-intellisense"></a>Usar IntelliSense

IntelliSense es una herramienta de Visual Studio que le ayuda a escribir código.

1. En *index.js*, vaya a la línea de código que contiene `res.render`.

1. Sitúe el cursor después de la cadena `data`, escriba `: get` e IntelliSense mostrará la función `getData` definida anteriormente en el código. Seleccione `getData`.

    ![Usar IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Quite la coma (`,`) antes de `"data"` y verá el resaltado de sintaxis de color verde en la expresión. Mueva el puntero sobre el resaltado de sintaxis.

    ![Ver error de sintaxis](../javascript/media/tutorial-nodejs-syntax-checking.png)

    La última línea de este mensaje indica que el intérprete de JavaScript esperaba una coma (`,`).

1. En el panel inferior, haga clic en la pestaña **Lista de errores**.

    Verá la advertencia y una descripción junto con el nombre de archivo y número de línea.

    ![Ver lista de errores](../javascript/media/tutorial-nodejs-error-list.png)

1. Corrija el código agregando la coma (`,`) antes de `"data"`.

    Una vez corregida, la línea de código debe ser similar a esta: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

Vamos a ejecutar la aplicación con el depurador de Visual Studio asociado. Antes de hacerlo, debe establecer un punto de interrupción.

1. En *index.js*, haga clic en el margen interno de la izquierda antes de la siguiente línea de código para establecer un punto de interrupción:

    `res.render('index', { title: 'Express', "data": getData() });`

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

    ![Establecer un punto de interrupción](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Seleccione el destino de depuración en la barra de herramientas de depuración, como Microsoft Edge o Chrome.

    ::: moniker range=">=vs-2019"
    ![Seleccionar el destino de depuración](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Seleccionar el destino de depuración](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Si Chrome está disponible en la máquina, pero no aparece como opción, elija **Explorar con** en la lista desplegable de destino de depuración y seleccione Chrome como el destino de explorador predeterminado (elija **Establecer como predeterminado**).

1. Presione **F5** (**Depurar** > **Iniciar depuración**) para ejecutar la aplicación.

    El depurador se detiene en el punto de interrupción definido. Ahora, puede inspeccionar el estado de la aplicación.

1. Mueva el cursor sobre `getData` para ver sus propiedades en una información sobre datos

    ![Inspeccionar variables](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Presione **F5** (**Depurar** > **Continuar**) para continuar.

    La aplicación se abre en un explorador.

    En la ventana del explorador, verá "Express" como el título y "Bienvenido a Express" en el primer párrafo.

1. Haga clic en los botones para mostrar diferentes imágenes.

    ![Aplicación en ejecución en el explorador](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Cierre el explorador web.

## <a name="optional-publish-to-azure-app-service"></a>(Opcional) Publicación en Azure App Service

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

   ![Publicación en Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Seleccione **Microsoft Azure App Service**.

    En el cuadro de diálogo **App Service**, puede iniciar sesión en la cuenta de Azure y conectarse a las suscripciones de Azure existentes.

1. Siga los pasos restantes para seleccionar una suscripción, elegir o crear un grupo de recursos, elegir o crear un plan de App Service y, después, siga los pasos cuando se le solicite para publicar en Azure. Para obtener instrucciones detalladas, vea [Publicación en el sitio web de Azure con Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. En la ventana **Salida** se muestra el progreso de la implementación en Azure.

    Después de una implementación correcta, la aplicación se abre en un explorador que se ejecuta en Azure App Service. Haga clic en un botón para mostrar una imagen.

   ![Aplicación que se ejecuta en Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Enhorabuena por completar este tutorial.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Implementación de una aplicación de App Service en Linux](../javascript/publish-nodejs-app-azure.md)