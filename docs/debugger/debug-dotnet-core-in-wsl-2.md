---
title: Depuración de aplicaciones de .NET Core en WSL 2
description: Aprenda a ejecutar y depurar las aplicaciones de .NET Core en WSL 2 sin salir de Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 6ae43b79b9db766d752a25fb538b7f208e6f5e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865623"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Depuración de aplicaciones de .NET Core en WSL 2 con Visual Studio

Puede ejecutar y depurar fácilmente sus aplicaciones de .NET Core en Linux sin salir de Visual Studio mediante WSL 2. Si es un desarrollador multiplataforma, puede usar este método como una forma sencilla de probar más sus entornos de destino.

Para un usuario de Windows .NET que tiene como destino Linux, WSL 2 representa un punto óptimo entre la productividad y el realismo de la producción. En Visual Studio, puede depurar en un entorno remoto de Linux mediante el [depurador remoto](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md), o bien con contenedores mediante las [herramientas de contenedor](../containers/overview.md). Si el realismo de la producción es su principal preocupación, debe usar una de las opciones anteriores. Cuando le preocupa más tener un bucle interno sencillo y rápido, WSL 2 es una opción excelente.

No tiene por qué elegir solo un método. Puede tener un perfil de inicio para Docker y otro para WSL 2 en el mismo proyecto y elegir el más adecuado para cada ejecución. Una vez implementada la aplicación, siempre puede usar el depurador remoto para asociarla si hay algún problema.

## <a name="prerequisites"></a>Requisitos previos

- Visual Studio 2019, versión 16.9 Preview 1 o versiones posteriores, con la depuración de .NET Core con el componente opcional para WSL 2.

  El componente opcional se incluye de forma predeterminada con las cargas de trabajo de desarrollo web, junto con las cargas de trabajo multiplataforma de .NET Core o con las cargas de ASP.NET. Debe instalar una de estas cargas de trabajo o ambas.

- Instalación de [WSL 2](/windows/wsl/about).

- Instalación de la [distribución](https://aka.ms/wslstore) que prefiera.

## <a name="start-debugging-with-wsl-2"></a>Inicio de la depuración con WSL 2

1. Después de instalar los componentes necesarios, abra una aplicación web de ASP.NET Core o una aplicación de consola de .NET Core en Visual Studio y verá un nuevo perfil de inicio denominado WSL 2:

   ![Perfil de inicio de WSL 2 en la lista de perfiles de inicio](media/linux-wsl2-debugging-select-launch-profile.png)

1. Seleccione este perfil para agregarlo a su archivo *launchSettings.json*.

   En el ejemplo siguiente se muestran algunos de los atributos clave del archivo.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Una vez que haya seleccionado el nuevo perfil, la extensión comprobará que la distribución de WSL 2 está configurada para ejecutar aplicaciones de .NET Core y le ayudará a instalar las dependencias que falten. Después de instalar estas dependencias, ya podrá depurar en WSL 2.

1. Inicie la depuración de la forma habitual; la aplicación se ejecutará en la distribución predeterminada de WSL 2.

   Una manera sencilla de asegurarse de que la aplicación se está ejecutando en Linux es comprobar el valor de `Environment.OSVersion`.

>[!NOTE]
> Solo se han probado y solo se admiten Ubuntu y Debian. Otras distribuciones admitidas por .NET Core deberían funcionar, pero se requiere la instalación manual del [runtime de .NET Core](https://aka.ms/wsldotnet) y de [Curl](https://curl.haxx.se/).

## <a name="choose-a-specific-distribution"></a>Elección de una distribución específica

De forma predeterminada, el perfil de inicio de WSL 2 usa la distribución predeterminada establecida en *wsl.exe*. Si quiere que el perfil de inicio tenga como destino una distribución específica, independientemente de la distribución predeterminada, puede modificar el perfil de inicio. Por ejemplo, si está depurando una aplicación web y quiere probarla en Ubuntu 20.04, el perfil de inicio tendrá el siguiente aspecto:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Varias distribuciones como destino

Para ir un paso más allá, si está trabajando en una aplicación que debe ejecutarse en varias distribuciones y quiere probarla en cada una de ellas de forma rápida, puede tener varios perfiles de inicio. Por ejemplo, si necesita probar su aplicación de consola en Debian, Ubuntu 18.04 y Ubuntu 20.04, puede usar los siguientes perfiles de Inicio:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Con estos perfiles de inicio, puede cambiar fácilmente de una distribución de destino a otra desde la comodidad de Visual Studio.

![Varios perfiles de inicio de WSL 2 en la lista de perfiles de inicio](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Configuración de WSL en el perfil de inicio

En la tabla siguiente se muestran los parámetros de configuración que se admite en el perfil de inicio.

|Nombre|Valor predeterminado|Propósito|¿Admite tokens?|
|-|-|-|-|
|executablePath|dotnet|El archivo ejecutable que se va a ejecutar.|Sí|
|commandLineArgs|Valor de la propiedad de MSBuild TargetPath asignada al entorno de WSL|Los argumentos de la línea de comandos que se pasan a executablePath.|Sí|
|workingDirectory|Para aplicaciones de consola: {*OutDir*}</br>Para aplicaciones web: {*ProjectDir*}|El directorio de trabajo en el que se va a iniciar la depuración.|Sí|
|environmentVariables||Los pares clave-valor de variables de entorno que se van a establecer para el proceso depurado.|Sí|
|setupScriptPath||El script que se va a ejecutar antes de la depuración. Resulta útil para ejecutar scripts como ~/.bash_profile.|Sí|
|distributionName||El nombre de la distribución de WSL que se va a usar.|No|
|launchBrowser|false|Indica si se va a iniciar o no un explorador.|No|
|launchUrl||La dirección URL que se iniciará si el valor de launchBrowser es true.|No|

Tokens admitidos:

{*ProjectDir*}: ruta de acceso al directorio del proyecto

{*OutDir*}: valor de la propiedad de MSBuild `OutDir`

>[!NOTE]
> Todas las rutas de acceso son para WSL, no para Windows.
