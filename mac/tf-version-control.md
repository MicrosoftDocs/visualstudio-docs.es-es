---
title: Control de versiones de Team Foundation (TFVC)
description: Conectarse desde Visual Studio para Mac a Team Foundation Server/Azure DevOps Services con Control de versiones de Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 04a251621af1086c15bafa15b7a9fe01f8dab5a8
ms.sourcegitcommit: 9d3529e40438ca45dcb0b31742c4cd5a89daa61e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398981"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation

> [!NOTE]
> Para una mejor experiencia de control de versiones en macOS, se recomienda usar Git en lugar del Control de versiones de Team Foundation (TFVC). Git es compatible con Visual Studio para Mac y es la opción predeterminada para los repositorios hospedados en Team Foundation Server (TFS)/Azure DevOps. Para más información sobre cómo usar Git con TFS/Azure DevOps, vea el artículo [Configurar un repositorio Git](/visualstudio/mac/set-up-git-repository).
> 
> Si anteriormente utilizaba la versión preliminar de la extensión TFVC para Visual Studio para Mac, ya no se admite en Visual Studio 2019 para Mac.

Azure Repos ofrece dos modelos de control de versiones: [Git](/azure/devops/repos/git/?view=azure-devops), un sistema de control de versiones distribuido, y el [Control de versiones de Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), un sistema de control de versiones centralizado.

Visual Studio para Mac proporciona compatibilidad total con repositorios Git, pero requiere algunas soluciones alternativas para trabajar con TFVC. Si usa TFVC para el control de versiones hoy en día, estas son algunas soluciones que puede usar para acceder al código fuente hospedado en TFVC:

* [Uso de Visual Studio Code y de la extensión de Azure Repos para una UI gráfica](#use-visual-studio-code-and-the-azure-repos-extension)
* [Conexión al repositorio con el cliente de la línea de comandos de Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

El resto de la información de este artículo lo guiará en las opciones indicadas anteriormente.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional o Enterprise para Mac, versión 7.8 y posterior.
* Azure DevOps Services, Team Foundation Server 2013 y versiones posteriores o Azure DevOps Server 2018 y versiones posteriores.
* Un proyecto en Azure DevOps Services o Team Foundation Server/Azure DevOps Server, configurado para que use el Control de versiones de Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Uso de Visual Studio Code y de la extensión de Azure Repos

Si le gusta trabajar con una interfaz gráfica para administrar los archivos en el control de versiones, la extensión de Azure Repos para Visual Studio Code proporciona una solución compatible de Microsoft. Para comenzar, descargue [Visual Studio Code](https://code.visualstudio.com) y, a continuación, obtenga información sobre cómo [configurar la extensión de Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Conexión con el cliente de la línea de comandos de Team Explorer Everywhere

Si se siente cómodo con el uso del Terminal de macOS, entonces el cliente de la línea de comandos de Team Explorer Everywhere (TEE-CLC) ofrece un método compatible de conexión al origen en TFVC.

Puede completar los pasos siguientes para configurar la conexión con TFVC y confirmar los cambios.

### <a name="setting-up-the-tee-clc"></a>Configuración de la TEE-CLC

Hay dos formas de instalar la TEE-CLC.

* Utilice Homebrew para instalar el cliente.
* También puede descargar el cliente e instalarlo manualmente.

La solución más sencilla es **usar HomeBrew**, que es un administrador de paquetes para macOS. Para instalar con este método:

1. Inicie la aplicación Terminal de macOS.
1. Instale Homebrew mediante el Terminal y las instrucciones que aparecen en la [página principal de Homebrew](https://brew.sh/).
1. Una vez instalado Homebrew, ejecute el siguiente comando desde el Terminal: `brew install tee-clc`.

Para **instalar la TEE-CLC manualmente**:

1. [Descargue la última versión de la TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) de la página de versiones del repositorio de GitHub para Team Explorer Everywhere (por ejemplo, tee-clc-14.134.0.zip en el momento en que se redactó este artículo).
1. Extraiga el contenido del archivo ZIP en una carpeta del disco.
1. Abra la aplicación Terminal de macOS y use el comando `cd` para cambiar a la carpeta utilizada en el paso anterior.
1. Desde dentro de la carpeta, ejecute el comando `./tf` para comprobar que se puede ejecutar el cliente de la línea de comandos; puede que se le pida que instale Java u otras dependencias.

Una vez instalada la TEE-CLC, puede ejecutar el comando `tf eula` para ver y aceptar el contrato de licencia del cliente.

Por último, para autenticarse en su entorno de TFS/Azure DevOps, deberá crear un token de acceso personal en el servidor. Obtenga más información sobre la [autenticación con tokens de acceso personal](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Al crear un token de acceso personal para usarlo con TFVC, asegúrese de proporcionar acceso total al configurar el token.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Uso de la TEE-CLC para conectarse a su repositorio

Para conectarse a su código fuente, primero debe crear un área de trabajo mediante el comando `tf workspace`. Por ejemplo, los siguientes comandos establecen conexión con una organización de Azure DevOps Services denominada "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

La configuración del entorno `TF_AUTO_SAVE_CREDENTIALS` se usa para guardar las credenciales, para que no se le pida que las escriba varias veces. Cuando se le pida un nombre de usuario, utilice el token de acceso personal que creó en la sección anterior y una contraseña en blanco.

Para crear una asignación de los archivos de origen a una carpeta local, se usa el comando `tf workfold`. En el ejemplo siguiente, se asociará una carpeta llamada "WebApp.Services" del proyecto de TFVC "MyRepository" y se configurará para que se copie en la carpeta local ~/Projects/ (por ejemplo, una carpeta "Proyectos" en la carpeta principal del usuario actual).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Por último, use el siguiente comando para obtener los archivos de origen del servidor y cópielos localmente:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Confirmación de los cambios mediante la TEE-CLC

Una vez realizados los cambios de los archivos en Visual Studio para Mac, puede cambiar al Terminal para registrar las modificaciones. El comando `tf add` se usa para agregar archivos a la lista de los cambios pendientes que se van a registrar y el comando `tf checkin` realiza el registro real en el servidor. El comando `checkin` incluye parámetros para agregar un comentario o asociar un elemento de trabajo relacionado. En el siguiente fragmento de código, se agregan al registro todos los archivos en una carpeta `WebApp.Services` de forma recursiva. A continuación, el código se registra con un comentario y se asocia con un elemento de trabajo con el identificador "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Para obtener más información sobre los comandos mencionados aquí u otros, puede usar el siguiente comando desde el Terminal:

`tf help`

### <a name="see-also"></a>Vea también

- [Develop and share your code in TFVC using Visual Studio (on Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs) (Desarrollar y compartir el código en TFVC con Visual Studio (en Windows))