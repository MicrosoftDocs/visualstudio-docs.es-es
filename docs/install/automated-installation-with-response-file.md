---
title: Automatizar la instalación de Visual Studio con un archivo de respuesta
description: Más información sobre cómo crear un archivo de respuesta JSON que permita automatizar la instalación de Visual Studio
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0029dc1599005cfe100bebbf9069dce672dd61b1
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282247"
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

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md)
