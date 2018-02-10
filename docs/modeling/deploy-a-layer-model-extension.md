---
title: "Implementar una extensión de modelo de capas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 311add860016c914aab232ffad6e3a4efadb15c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-a-layer-model-extension"></a>Implementar una extensión del modelo de capas
Otros usuarios de Visual Studio pueden instalar las extensiones de modelado de capas que se crean mediante Visual Studio.  
  
## <a name="installing-your-extension"></a>Instalar la extensión  
 La extensión está compilada en un archivo VSIX que se puede instalar en otros equipos. También se puede instalar en el equipo de desarrollo, para que la extensión esté disponible en la instancia principal de Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Para instalar la extensión  
  
1.  En el proyecto que contiene **source.vsix.manifest**, abra **bin\\ \***  en el Explorador de archivos.  
  
2.  Copia la  **\*.vsix** archivo en el equipo en el que va a instalar la extensión.  
  
3.  En el equipo de destino, haga doble clic en el * archivo .vsix en el Explorador de Windows.  
  
     Se abre el instalador VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión  
  
1.  En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.  
  
2.  Haga clic en el nombre de la extensión y, a continuación, haga clic en **desinstalar**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalar una extensión en un servidor de Team Foundation Build Server  
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] servidores no suelen tengan instalado Visual Studio y, por lo que no se puede instalar la extensión VSIX haciendo doble clic en él. La instalación de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] incluye algunos componentes que permiten ejecutar una extensión VSIX, pero esta se debe instalar manualmente.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Para instalar la extensión por capas en un servidor de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server  
  
1.  Copia la **.vsix** archivos desde el equipo de desarrollo para la [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] equipo.  
  
     Coloque el archivo VSIX en una de las siguientes ubicaciones:  
  
    -   Para instalarlo para todos los usuarios y servicios:  
  
         %ProgramFiles%\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft  
  
    -   Para instalarlo solo para el servicio de red que ejecuta [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Si ha configurado [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] para ejecutarlo en modo interactivo como un usuario concreto, puede instalarlo solo para ese usuario:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        >  Suele ser % LocalAppData % *DriveName*: los usuarios*nombre de usuario*AppDataLocal.  
  
2.  Expanda cada archivo VSIX en una carpeta en la misma ubicación:  
  
    1.  Cambie la extensión de nombre de archivo de **.vsix** a **.zip**.  
  
    2.  Extraiga el contenido del archivo .zip a una carpeta.  
  
    3.  Elimine el archivo .zip  
  
3.  Reinicie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
