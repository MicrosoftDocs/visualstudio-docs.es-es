---
title: Creación de una aplicación Vue.js mediante Node.js
description: Puede crear aplicaciones de Node.js en Visual Studio mediante el marco de Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a1c9de1c65c5f3f780e6ea4374fa7d96f436f514
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227766"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Crear una aplicación Vue.js con Herramientas de Node.js para Visual Studio

Visual Studio 2017 incluye compatibilidad mejorada con el marco de [Vue.js](https://vuejs.org/), lo que mejora la experiencia de desarrollo al crear una aplicación con Vue.js, JavaScript y TypeScript.

Las siguientes características nuevas admiten el desarrollo de aplicaciones Vue.js en Visual Studio:

* Compatibilidad con bloques de script, estilos y plantillas en archivos *.vue*
* Reconocimiento del atributo `lang` en archivos *.vue*
* Plantillas de proyecto y archivo de Vue.js

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio 2017 versión 15.8 Preview 3 o posterior, y la carga de trabajo de **desarrollo de Node.js**.

    > [!IMPORTANT]
    > En este artículo se necesitan características que solo están disponibles a partir de Visual Studio 2017 versión 15.8 Preview 3.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  para instalarlo de forma gratuita.

    Si necesita instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto** (seleccione **Archivo** > **Nuevo** > **Proyecto**). Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

* Para crear el proyecto de ASP.NET Core, debe tener instaladas las cargas de trabajo de desarrollo multiplataforma de ASP.NET y .NET Core.

* Debe tener instalado el runtime de Node.js.

    Si todavía no lo tiene instalado, instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/). En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta ningún runtime instalado, puede configurar el proyecto para que haga referencia al runtime instalado en la página de propiedades. (Después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**).

## <a name="create-a-vuejs-project-using-a-template"></a>Crear un proyecto de Vue.js con una plantilla

Puede usar las nuevas plantillas de Vue.js para crear un proyecto. La plantilla es la manera más fácil de empezar a trabajar. Para conocer los pasos detallados, vea [Usar Visual Studio para crear la primera aplicación Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Crear un proyecto de Vue.js con ASP.NET Core y la CLI de Vue

Vue.js proporciona una CLI oficial para aplicar scaffolding a proyectos rápidamente. Si quiere usar la CLI para crear la aplicación, siga los pasos de este artículo para configurar el entorno de desarrollo.

> [!IMPORTANT]
> En estos pasos se da por hecho que ya tiene cierta experiencia con el marco de Vue.js. Si no es así, visite [Vue.js](https://vuejs.org/) para obtener más información sobre el marco.

### <a name="create-a-new-aspnet-core-project"></a>Crear un nuevo proyecto de ASP.NET Core

En este ejemplo, use una aplicación vacía ASP.NET Core (C#). Pero puede elegir entre una serie de proyectos y lenguajes de programación.

#### <a name="create-an-empty-project"></a>Crear un proyecto vacío

1. Abra Visual Studio y elija **Archivo** > **Nuevo** > **Proyecto** en el menú principal.

1. En **Visual C#** > **Web**, elija **Aplicación web ASP.NET Core** y luego haga clic en **Aceptar**.

    Si no ve la plantilla de proyecto **Aplicación web ASP.NET Core**, primero debe instalar la carga de trabajo de **desarrollo de ASP.NET y web** y la carga de trabajo de desarrollo de .**NET Core**. Para instalar las cargas de trabajo, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto** (seleccione **Archivo** > **Nuevo** > **Proyecto**). Se iniciará el Instalador de Visual Studio. Seleccione las cargas de trabajo necesarias.

1. Seleccione **Vacío** y después haga clic en **Aceptar**.

    Visual Studio crea el proyecto, con lo que se abre el Explorador de soluciones (panel derecho).

#### <a name="configure-the-project-startup-file"></a>Configurar el archivo de inicio del proyecto

* Abra el archivo *./Startup.cs* y agregue las siguientes líneas al método Configure:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Instalar la CLI de Vue

Para instalar el módulo de npm vue-cli, abra un símbolo del sistema y escriba `npm install --g vue-cli` o `npm install -g @vue/cli` para la versión 3.0 (actualmente en versión beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Aplicar scaffolding a una nueva aplicación de cliente mediante la CLI de Vue

1. Vaya al símbolo del sistema y cambie el directorio actual a la carpeta raíz del proyecto.

1. Escriba `vue init webpack ClientApp` y siga los pasos cuando se le solicite que responda a otras preguntas.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modificar la configuración de webpack para que la salida de los archivos compilados sea wwwroot

* Abra el archivo *./ClientApp/config/index.js* y cambie `build.index` y `build.assetsRoot` a la ruta wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>Indicar el proyecto para compilar la aplicación cliente cada vez que se produzca una compilación

1. En Visual Studio, vaya a **Proyecto** > **Propiedades** > **Eventos de compilación**.

1. En **Línea de comandos del evento anterior a la compilación**, escriba `npm --prefix ./ClientApp run build`.

#### <a name="configure-webpacks-output-module-names"></a>Configurar nombres de módulos de salida de webpack

* Abra el archivo *./ClientApp/build/webpack.base.conf.js* y agregue las siguientes propiedades a la propiedad de salida:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Agregar compatibilidad con TypeScript mediante la CLI de Vue

Estos pasos requieren vue-cli 3.0, que actualmente se encuentra en versión beta.

1. Vaya al símbolo del sistema y cambie el directorio actual a la carpeta raíz del proyecto.

1. Escriba `vue create ClientApp` y luego elija **Manually select features** (Seleccionar características manualmente).

1. Elija **Typescript** y luego seleccione otras opciones que quiera.

1. Siga los pasos restantes y responda a las preguntas.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Configurar un proyecto de Vue.js para TypeScript

1. Abra el archivo *./ClientApp/tsconfig.json* y agregue `noEmit:true` a las opciones del compilador.

    Al establecer esta opción, evita colapsar el proyecto cada vez que se compila en Visual Studio.

1. Luego cree un archivo *vue.config.js* en *./ClientApp/* y agregue el código siguiente.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    El código anterior configura webpack y establece la carpeta wwwroot.

#### <a name="build-with-vue-cli-30"></a>Compilar con vue-cli 3.0

Un problema desconocido con vue-cli 3.0 evita la automatización del proceso de compilación. Cada vez que se intenta actualizar la carpeta wwwroot, debe ejecutar el comando `npm run build` en la carpeta ClientApp.

## <a name="limitations"></a>Limitaciones

* El atributo `lang` solo admite los lenguajes JavaScript y TypeScript. Los valores aceptados son: js, jsx, ts y tsx.
* El atributo `lang` no funciona con etiquetas de estilo o plantilla.
* La depuración de bloques de script en archivos *.vue* no se admite debido a su naturaleza procesada previamente.
* TypeScript no reconoce los archivos *.vue* como módulos. Se necesita un archivo que contenga código como el siguiente para indicar a TypeScript el aspecto de los archivos *.vue* (la plantilla vue-cli 3.0 ya incluye este archivo).

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* La ejecución del comando `npm run build` como un evento anterior a la compilación en las propiedades del proyecto no funciona cuando se usa vue-cli 3.0.

## <a name="see-also"></a>Vea también

- [Guía de introducción de Vue](https://vuejs.org/v2/guide).
- [Proyecto de CLI de Vue](https://github.com/vuejs/vue-cli).
- [Documentación de configuración de Webpack](https://webpack.js.org/configuration/).
