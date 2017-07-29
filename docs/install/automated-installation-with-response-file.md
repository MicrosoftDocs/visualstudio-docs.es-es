---
title: "Automatización de la instalación de Visual Studio con un archivo de respuesta | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: es-es
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Definición de la configuración en un archivo de respuesta
Los administradores que implementan Visual Studio pueden especificar un archivo de respuesta mediante el parámetro `--in`, por ejemplo:

```
vs_enterprise.exe --in customInstall.json
```

Los archivos de respuesta son archivos [JSON](http://json-schema.org/) cuyo contenido reflejan los argumentos de línea de comandos.  En general, si un parámetro de línea de comandos no toma ningún argumento (por ejemplo, `--quiet`, `--passive`, etc.), el valor del archivo de respuesta debe ser true/false.  Si toma un argumento (por ejemplo, `--installPath <dir>`), el valor del archivo de respuesta debe ser una cadena.  Si toma un argumento y puede aparecer más de una vez en la línea de comandos (por ejemplo, `--add <id>`), debe ser una matriz de cadenas.

Los parámetros especificados en la línea de comandos invalidan la configuración del archivo de respuesta, excepto en el caso de parámetros que toman varias entradas (por ejemplo, `--add`), donde las entradas suministradas en la línea de comandos se combinan con la configuración del archivo de respuesta.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Establecimiento de una configuración predeterminada para Visual Studio

Si creó una caché de diseño de red con `--layout`, se crea un archivo `response.json` inicial en el diseño.

Los administradores que crean un diseño pueden modificar el archivo `response.json` en el diseño para controlar la configuración predeterminada que verán sus usuarios al instalar Visual Studio a partir del diseño.  Por ejemplo, si un administrador desea que se instalen de forma predeterminada las cargas de trabajo y los componentes seleccionados, puede configurar un archivo `response.json` para agregarlos.

Cuando se ejecuta la instalación de Visual Studio desde una carpeta de diseño, se usará _automáticamente_ el archivo de respuesta de la carpeta de diseño.  No es necesario usar la opción `--in`.

Puede actualizar el archivo `response.json` que se crea en una carpeta de diseño sin conexión para definir la configuración predeterminada de los usuarios que realizan la instalación desde este diseño. **Sin embargo, es fundamental que deje las propiedades existentes que se definieron cuando se creó el diseño.**

El archivo base `response.json` del diseño será parecido a este pero con el valor del producto y el canal que va a instalar:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Ejemplo de contenido del archivo de respuesta de diseño
En este ejemplo se instalará Visual Studio Enterprise con seis cargas de trabajo y componentes comunes, con los idiomas inglés y francés para la interfaz de usuario. Puede usarlo como plantilla; simplemente cambie las cargas de trabajo y los componentes por los que quiere instalar.

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

