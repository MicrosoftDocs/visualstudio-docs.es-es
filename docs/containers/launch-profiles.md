---
title: Administración de perfiles de inicio para proyectos de Docker Compose
description: Obtenga información sobre cómo usar perfiles de inicio de Docker Compose y controlar qué servicios se inician al usar Docker Compose en Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433706"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Administración de perfiles de inicio para Docker Compose

Si tiene una aplicación que consta de varios servicios y usa Docker Compose, puede configurar qué servicios se ejecutan y depuran mediante la creación o edición de un perfil de inicio existente en la configuración de inicio de Docker Compose. Los perfiles de inicio permiten ejecutar de forma dinámica solo los servicios relevantes para el escenario actual. Puede crear y seleccionar perfiles de inicio para personalizar la experiencia de depuración y establecer acciones de inicio específicas, como `Browser Launch URL`. Además, tendrá la opción de elegir cada servicio individualmente o elegir un perfil de Docker Compose, que también examina el archivo de Compose para determinar el grupo de servicios que se va a ejecutar.

Para obtener información sobre los perfiles de inicio de Docker Compose, vea [Uso de perfiles con Compose](https://docs.docker.com/compose/profiles/).
 
## <a name="prerequisites"></a>Prerrequisitos

- [Visual Studio 2019, versión 16.10](https://visualstudio.microsoft.com/vs/) o posterior
- Una solución con [Orquestación de contenedores con Docker Compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Administración de la configuración de inicio

Considere el siguiente proyecto de Docker Compose en el que *docker-compose.yml* tiene cinco servicios y tres perfiles de Compose (web, web1 y web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Hay algunas opciones para abrir el cuadro de diálogo de configuración de inicio de Docker Compose:
- En Visual Studio, elija **Depurar** > **Administrar la configuración de inicio de Docker Compose**:

    ![Captura de pantalla del elemento de menú Administrar la configuración de Compose de Depurar](media/launch-settings/debug-dropdown-manage-compose.png)

- Haga clic con el botón derecho en el proyecto `docker-compose` de Visual Studio y seleccione **Administrar la configuración de inicio de Docker Compose**.

    ![Captura de pantalla del elemento de menú contextual](media/launch-settings/launch-settings-context-menu.png)

- Use el inicio rápido (**Ctrl**+**Q**) y busque **Docker Compose** para encontrar el comando mencionado anteriormente.

En el ejemplo siguiente, se selecciona el perfil de Compose `web1`, que filtra la lista **Servicios** solo a tres de los cinco incluidos en ese perfil:

!["Captura de pantalla del cuadro de diálogo de configuración de inicio"](media/launch-settings/launch-settings-create-profile.png)

La sección Perfiles de Docker Compose solo aparece si hay perfiles definidos en los archivos *docker-compose.yml.*

En el ejemplo siguiente se muestra cómo seleccionar entre servicios individuales en lugar de filtrar por los servicios de un perfil de Compose. Aquí se muestra el aspecto del cuadro de diálogo si ha creado un perfil de inicio denominado `test2` que solo inicia dos de los cinco servicios, `webapplication1` con depuración y `webapplication2` sin depuración.  Este perfil de inicio también inicia un explorador cuando se inicia la aplicación y lo abre en la página principal de `webapplication1`. 

![Captura de pantalla del cuadro de diálogo de configuración de inicio con algunos servicios no seleccionados](media/launch-settings/launch-settings-selected.png)

Y esta información se guardará en *launchSettings.js* como se muestra a continuación.

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Creación de un perfil de inicio en el que se usa un perfil de Docker Compose

También puede personalizar aún más los comportamientos de inicio si crea perfiles de inicio de Visual Studio en los que se usan los perfiles de Compose.

Para crear otro perfil que use el de Compose, seleccione **Use Docker Compose profiles** (Usar perfiles de Docker Compose) y elija `web1`. Ahora, el perfil de inicio incluye tres servicios: `webapplication1` (que pertenece a los perfiles de Compose `web` y `web1`), `external1` y `external2`. De forma predeterminada, los servicios sin código fuente como `external1` y `external2` tienen la acción predeterminada **Iniciar sin depurar**. Las aplicaciones de .NET con código fuente tendrán como valor predeterminado **Iniciar depuración**.

> [!IMPORTANT]
> Si un servicio no especifica un perfil de Compose, se incluirá implícitamente en todos los perfiles de Compose.

![Captura de pantalla del cuadro de diálogo de configuración de inicio con otro perfil creado](media/launch-settings/launch-settings-create-profile.png)

Esta información se guardará como se muestra en el código siguiente. La configuración del servicio y su acción predeterminada no se guardan a menos que cambie la acción predeterminada.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

También puede cambiar la acción de webapplication1 a **Iniciar sin depurar**. La configuración de *launchSettings.json* es similar al código siguiente:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Propiedades

Esta es una descripción de cada propiedad de *launchSettings.json*:

|Propiedad| Descripción|
| - | - |
|commandName| Nombre del comando. El valor predeterminado es "DockerCompose"|
|commandVersion| Número de versión que se usa para administrar el esquema del perfil de inicio de Docker Compose.|
|composeProfile| Propiedad primaria que define la definición del perfil de inicio. Sus propiedades secundarias son `includes` y `serviceActions`|
|composeProfile: includes | Lista de los nombres de perfil de Compose que componen un perfil de inicio.|
|composeProfile: serviceActions | Enumera los perfiles de Compose seleccionados, los servicios y la acción de inicio de cada servicio.|
|serviceActions | Enumera los servicios seleccionados y la acción de inicio.|
|composeLaunchServiceName| Si se especifican DockerLaunchAction o DockerLaunchBrowser, DockerServiceName es el nombre del servicio que se debe iniciar. Use esta propiedad para determinar qué servicio dentro del archivo Docker Compose se va a iniciar.|
|composeLaunchAction| Especifica la acción de inicio que se va a realizar al presionar **F5** o **Ctrl**+**F5**. Los valores permitidos son None, LaunchBrowser y LaunchWCFTestClient.|
|composeLaunchUrl| Esta dirección URL se usa al iniciar el explorador. Los tokens de reemplazo válidos son "{ServiceIPAddress}", "{ServicePort}" y "{Scheme}". Por ejemplo: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo funciona Container Tools, lea [Introducción a la compilación y la depuración en las herramientas de contenedor de Visual Studio](container-build.md).

## <a name="see-also"></a>Vea también

- [Configuración de inicio de las herramientas de contenedor de Visual Studio](container-launch-settings.md)

- [Configuración de compilación de Docker Compose](docker-compose-properties.md)
