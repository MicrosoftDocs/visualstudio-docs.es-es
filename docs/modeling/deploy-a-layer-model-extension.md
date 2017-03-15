---
title: "Implementar una extensión del modelo de capas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>Implementar una extensión del modelo de capas
Otros usuarios de Visual Studio pueden instalar las extensiones de modelado de capas que se crean mediante Visual Studio.  
  
## <a name="installing-your-extension"></a>Instalar la extensión  
 La extensión está compilada en un archivo VSIX que se puede instalar en otros equipos. También se puede instalar en el equipo de desarrollo, para que la extensión esté disponible en la instancia principal de Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Para instalar la extensión  
  
1.  En el proyecto que contiene **source.vsix.manifest**, abra **bin\\ \* ** en el Explorador de archivos.  
  
2.  Copia la ** \*.vsix** archivos en el equipo en el que desea instalar la extensión.  
  
3.  En el equipo de destino, haga doble clic en el * archivo .vsix en el Explorador de Windows.  
  
     Se abre el instalador VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar la extensión  
  
1.  En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.  
  
2.  Haga clic en el nombre de la extensión y, a continuación, haga clic en **desinstalar**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalar una extensión en un servidor de Team Foundation Build Server  
 Los servidores de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] no tienen normalmente Visual Studio instalado y, por lo tanto, VSIX no se puede instalar haciendo doble clic en él. La instalación de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] incluye algunos componentes que permiten ejecutar una extensión VSIX, pero esta se debe instalar manualmente.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Para instalar la extensión por capas en un servidor de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server  
  
1.  Copia la **.vsix** archivos del equipo de desarrollo para la [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] equipo.  
  
     Coloque el archivo VSIX en una de las siguientes ubicaciones:  
  
    -   Para instalarlo para todos los usuarios y servicios:  
  
         %ProgramFiles%\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft  
  
    -   Para instalarlo solo para el servicio de red que ejecuta [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [versión]  
  
    -   Si ha configurado [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] para ejecutarlo en modo interactivo como un usuario concreto, puede instalarlo solo para ese usuario:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [versión]  
  
        > [!NOTE]
        >  % LocalAppData % suele *DriveName*: usuarios*nombre de usuario*AppDataLocal.  
  
2.  Expanda cada archivo VSIX en una carpeta en la misma ubicación:  
  
    1.  Cambiar la extensión de nombre de archivo de **.vsix** a **.zip**.  
  
    2.  Extraiga el contenido del archivo .zip a una carpeta.  
  
    3.  Elimine el archivo .zip  
  
3.  Reinicie [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].

