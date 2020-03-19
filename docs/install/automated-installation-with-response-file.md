---
title: Automatización de la instalación con un archivo de respuesta
description: Más información sobre cómo crear un archivo de respuesta JSON que permita automatizar la instalación de Visual Studio
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecdda55bbe4e79af01f8fb9a9a2b77f775548b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115232"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Definición de la configuración en un archivo de respuesta

Los administradores que implementan Visual Studio pueden especificar un archivo de respuesta con el parámetro `--in`, como en el ejemplo siguiente:

```cmd
vs_enterprise.exe --in customInstall.json
```

Los archivos de respuesta son archivos [JSON](http://json-schema.org/) cuyo contenido reflejan los argumentos de línea de comandos.  En general, si un parámetro de línea de comandos no toma ningún argumento (por ejemplo, `--quiet`, `--passive`, etc.), el valor del archivo de respuesta debe ser "true" o "false".  Si toma un argumento (por ejemplo, `--installPath <dir>`), el valor del archivo de respuesta debe ser una cadena.  Si toma un argumento y puede aparecer más de una vez en la línea de comandos (por ejemplo, `--add <id>`), debe ser una matriz de cadenas.

Los parámetros que se especifican en la línea de comandos invalidan la configuración a partir del archivo de respuesta, excepto cuando los parámetros toman varias entradas (por ejemplo, `--add`). Cuando tiene varias entradas, las entradas proporcionadas en la línea de comandos se combinan con la configuración del archivo de respuesta.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Establecimiento de una configuración predeterminada para Visual Studio

Si creó una caché de diseño de red con `--layout`, se crea un archivo `response.json` inicial en el diseño. Si crea un diseño parcial, este archivo de respuesta incluye las cargas de trabajo y los idiomas que se han incluido en el diseño.  Al ejecutar la instalación desde este diseño se usa automáticamente este archivo response.json, que selecciona las cargas de trabajo y los componentes incluidos en el diseño.  Los usuarios pueden seleccionar o anular la selección de cualquier carga de trabajo en la interfaz de usuario de instalación antes de instalar Visual Studio.

Los administradores que crean un diseño pueden modificar el archivo `response.json` en el diseño para controlar la configuración predeterminada que ven sus usuarios al instalar Visual Studio a partir del diseño.  Por ejemplo, si un administrador quiere que se instalen de manera predeterminada las cargas de trabajo y los componentes específicos, puede configurar un archivo `response.json` para agregarlos.

Cuando se ejecuta la instalación de Visual Studio desde una carpeta de diseño, usa _automáticamente_ el archivo de respuesta de la carpeta de diseño.  No tiene que usar la opción `--in`.

Puede actualizar el archivo `response.json` que se crea en una carpeta de diseño sin conexión para definir la configuración predeterminada de los usuarios que realizan la instalación desde este diseño.

> [!WARNING]
> Es fundamental que deje las propiedades existentes que se han definido cuando se ha creado el diseño.

El archivo `response.json` base de un diseño debe tener un aspecto similar al ejemplo siguiente, salvo por el hecho de que incluiría el valor del producto y el canal que quiere instalar:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Cuando crea o actualiza un diseño, también se crea un archivo response.template.json.  Este archivo contiene todos los identificadores de idioma, componentes y carga de trabajo que pueden usarse.  Este archivo se proporciona como una plantilla para todo lo que podría incluirse en una instalación personalizada.  Los administradores pueden usar este archivo como un punto inicial para un archivo de respuesta personalizado.  Simplemente quite los identificadores de lo que no quiere instalar y guárdelo en su propio archivo de respuesta.  No personalice el archivo response.template.json o sus cambios se perderán cuando se actualice el diseño.

## <a name="example-layout-response-file-content"></a>Ejemplo de contenido del archivo de respuesta de diseño

En el siguiente ejemplo se instala Visual Studio Enterprise con seis cargas de trabajo y componentes comunes, con los idiomas inglés y francés para la interfaz de usuario. Puede usar este ejemplo como una plantilla; simplemente cambie las cargas de trabajo y los componentes que quiere instalar:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
