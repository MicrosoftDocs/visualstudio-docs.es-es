---
title: Implementar una extensión de modelo de capas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669862"
---
# <a name="deploy-a-layer-model-extension"></a>Implementar una extensión del modelo de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Otros usuarios de Visual Studio pueden instalar las extensiones de modelado de capas que se crean mediante Visual Studio.

## <a name="installing-your-extension"></a>Instalar la extensión
 La extensión está compilada en un archivo VSIX que se puede instalar en otros equipos. También se puede instalar en el equipo de desarrollo, para que la extensión esté disponible en la instancia principal de Visual Studio.

#### <a name="to-install-the-extension"></a>Para instalar la extensión

1. En el proyecto que contiene **source. vsix. manifest**, abra **bin \\ \\** * en el explorador de archivos.

2. Copie el archivo **\*. vsix** en el equipo en el que desea instalar la extensión.

3. En el equipo de destino, haga doble clic en el * archivo .vsix en el Explorador de Windows.

    Se abre el instalador VSIX.

#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Haga clic en el nombre de la extensión y, a continuación, haga clic en **desinstalar**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalar una extensión en un servidor de Team Foundation Build Server
 Los servidores de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] no tienen normalmente Visual Studio instalado y, por lo tanto, VSIX no se puede instalar haciendo doble clic en él. La instalación de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] incluye algunos componentes que permiten ejecutar una extensión VSIX, pero esta se debe instalar manualmente.

#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>Para instalar la extensión por capas en un servidor de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] Server

1. Copie los archivos **. vsix** del equipo de desarrollo en el [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] equipo.

     Coloque el archivo VSIX en una de las siguientes ubicaciones:

    - Para instalarlo para todos los usuarios y servicios:

         %ProgramFiles%\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft

    - Para instalarlo solo para el servicio de red que ejecuta [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [versión] \Extensions\Microsoft

    - Si ha configurado [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] para ejecutarlo en modo interactivo como un usuario concreto, puede instalarlo solo para ese usuario:

         %LocalAppData%\Microsoft\VisualStudio \\ [versión] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData *% suele ser*el nombre de*usuario*AppDataLocal.

2. Expanda cada archivo VSIX en una carpeta en la misma ubicación:

    1. Cambie la extensión de nombre de archivo de **. vsix** a **. zip**.

    2. Extraiga el contenido del archivo .zip a una carpeta.

    3. Elimine el archivo .zip

3. Reinicie [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].
