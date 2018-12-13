---
title: Implementar una extensión del modelo de capas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 98697642135627173c5a6f31e90bf1dd1d0caeaf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307757"
---
# <a name="deploy-a-layer-model-extension"></a>Implementar una extensión del modelo de capas

Otros usuarios de Visual Studio pueden instalar las extensiones de modelado de capas que se crean mediante Visual Studio.

## <a name="install-your-extension"></a>Instalar la extensión

La extensión está compilada en un archivo VSIX que se puede instalar en otros equipos. También se puede instalar en el equipo de desarrollo, para que la extensión esté disponible en la instancia principal de Visual Studio.

### <a name="to-install-the-extension"></a>Para instalar la extensión

1. En el proyecto que contiene **source.vsix.manifest**, abra el *bin* directorio en el Explorador de archivos.

2. Copia el  **\*.vsix** archivo en el equipo en el que desea instalar la extensión.

3. En el equipo de destino, haga doble clic en el * archivo .vsix en el Explorador de Windows.

    Se abre el instalador VSIX.

### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1.  En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

2.  Haga clic en el nombre de la extensión y, a continuación, haga clic en **desinstalar**.

## <a name="install-an-extension-on-team-foundation-server"></a>Instalar una extensión de Team Foundation Server

Servidores de Team Foundation Server no suelen tengan instalado Visual Studio y, por lo que no se puede instalar la extensión VSIX haciendo doble clic en él. Debe instalar la extensión manualmente.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Para instalar la extensión de capas en un servidor de Team Foundation Server

1.  Copia el. *vsix* archivos del equipo de desarrollo en el equipo de Team Foundation Server (TFS).

     Coloque el archivo VSIX en una de las siguientes ubicaciones:

    -   Para instalarlo para todos los usuarios y servicios:

         %ProgramFiles%\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft

    -   Para instalar solo para el servicio de red que se ejecuta la compilación:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Si ha configurado la compilación se ejecute en modo interactivo como un usuario concreto, puede instalar solo para ese usuario:

         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [versión]

2.  Expanda cada archivo VSIX en una carpeta en la misma ubicación:

    1.  Cambiar la extensión de nombre de archivo de **.vsix** a **.zip**.

    2.  Extraiga el contenido del archivo .zip a una carpeta.

    3.  Elimine el archivo .zip

3.  Reinicie TFS.
