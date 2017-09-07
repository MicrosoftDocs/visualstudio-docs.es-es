---
title: "Automatización de la instalación de Visual Studio con un archivo de respuesta | Microsoft Docs"
description: "Más información sobre cómo crear un archivo de respuesta JSON que permita automatizar la instalación de Visual Studio"
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 5c8aaf24a1952847c593d5eb70f7c94208310174
ms.contentlocale: es-es
ms.lasthandoff: 08/14/2017

---

# <a name="how-to-define-settings-in-a-response-file"></a>Definición de la configuración en un archivo de respuesta
Los administradores que implementan Visual Studio pueden especificar un archivo de respuesta con el parámetro `--in`, como en el ejemplo siguiente:

```
vs_enterprise.exe --in customInstall.json
```

Los archivos de respuesta son archivos [JSON](http://json-schema.org/) cuyo contenido reflejan los argumentos de línea de comandos.  En general, si un parámetro de línea de comandos no toma ningún argumento (por ejemplo, `--quiet`, `--passive`, etc.), el valor del archivo de respuesta debe ser "true" o "false".  Si toma un argumento (por ejemplo, `--installPath <dir>`), el valor del archivo de respuesta debe ser una cadena.  Si toma un argumento y puede aparecer más de una vez en la línea de comandos (por ejemplo, `--add <id>`), debe ser una matriz de cadenas.

Los parámetros que se especifican en la línea de comandos invalidan la configuración a partir del archivo de respuesta, excepto cuando los parámetros toman varias entradas (por ejemplo, `--add`). Cuando tiene varias entradas, las entradas proporcionadas en la línea de comandos se combinan con la configuración del archivo de respuesta.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Establecimiento de una configuración predeterminada para Visual Studio

Si creó una caché de diseño de red con `--layout`, se crea un archivo `response.json` inicial en el diseño. Si crea un diseño parcial, este archivo de respuesta incluye las cargas de trabajo y los idiomas que se han incluido en el diseño.  Al ejecutar la instalación desde este diseño se usa automáticamente este archivo response.json, que selecciona las cargas de trabajo y los componentes incluidos en el diseño.  Los usuarios pueden seleccionar o anular la selección de cualquier carga de trabajo en la interfaz de usuario de instalación antes de instalar Visual Studio. 

Los administradores que crean un diseño pueden modificar el archivo `response.json` en el diseño para controlar la configuración predeterminada que ven sus usuarios al instalar Visual Studio a partir del diseño.  Por ejemplo, si un administrador quiere que se instalen de manera predeterminada las cargas de trabajo y los componentes específicos, puede configurar un archivo `response.json` para agregarlos.

Cuando se ejecuta la instalación de Visual Studio desde una carpeta de diseño, usa _automáticamente_ el archivo de respuesta de la carpeta de diseño.  No tiene que usar la opción `--in`.

Puede actualizar el archivo `response.json` que se crea en una carpeta de diseño sin conexión para definir la configuración predeterminada de los usuarios que realizan la instalación desde este diseño.

> [!WARNING]
> Es fundamental que deje las propiedades existentes que se han definido cuando se ha creado el diseño.

El archivo `response.json` base de un diseño debe tener un aspecto similar al ejemplo siguiente, salvo por el hecho de que incluiría el valor del producto y el canal que quiere instalar:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```
Cuando crea o actualiza un diseño, también se crea un archivo response.template.json.  Este archivo contiene todos los identificadores de idioma, componentes y carga de trabajo que pueden usarse.  Este archivo se proporciona como una plantilla para todo lo que podría incluirse en una instalación personalizada.  Los administradores pueden usar este archivo como un punto inicial para un archivo de respuesta personalizado.  Simplemente quite los identificadores de lo que no quiere instalar y guárdelo en su propio archivo de respuesta.  No personalice el archivo response.template.json o sus cambios se perderán cuando se actualice el diseño. 

## <a name="example-layout-response-file-content"></a>Ejemplo de contenido del archivo de respuesta de diseño
En el siguiente ejemplo se instala Visual Studio Enterprise con seis cargas de trabajo y componentes comunes, con los idiomas inglés y francés para la interfaz de usuario. Puede usar este ejemplo como una plantilla; simplemente cambie las cargas de trabajo y los componentes que quiere instalar:

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
## <a name="see-also"></a>Vea también
* [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md)

