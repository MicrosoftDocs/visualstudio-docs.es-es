---
title: Instalación del SDK de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843428"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalación de Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalación del SDK de Visual Studio como parte de una instalación de Visual Studio  
 Si desea incluir VSSDK en la instalación de Visual Studio, debe realizar una instalación personalizada.  
  
> [!NOTE]
> En el ejecutable de instalación, el SDK de Visual Studio se denomina **herramientas de extensibilidad de Visual Studio**.  
  
1. Inicie la instalación de Visual Studio 2015. Puede instalar cualquier edición de Visual Studio excepto Express.  
  
2. En la primera pantalla, seleccione **personalizada**, no **predeterminada**. Haga clic en **Siguiente**.  
  
3. Debería ver una vista de árbol de características personalizadas. Abra **herramientas comunes**. Debería ver **herramientas de extensibilidad de Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Compruebe **herramientas de extensibilidad de Visual Studio** , haga clic en **siguiente** y continúe con la instalación.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalación del SDK de Visual Studio después de instalar Visual Studio  
 Si decide instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, debe seguir el procedimiento siguiente:  
  
1. Vaya a **Panel de control/programas/programas y características**y busque **Visual Studio 2015**. Puede instalar el SDK de Visual Studio para cualquier edición de Visual Studio 2015 excepto Express.  
  
2. Haga clic con el botón secundario en **Visual Studio 2015**y, a continuación, haga clic en **cambiar**. Debería ver la página de instalación.  
  
3. Siga el mismo procedimiento que en **instalar el SDK de Visual Studio como parte de una instalación de Visual Studio** anterior.  
  
4. Haga clic en el vínculo **herramientas de extensibilidad de Visual Studio** para instalar el SDK de Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalación del SDK de Visual Studio desde una solución  
 Si abre una solución con un proyecto de extensibilidad sin instalar primero el VSSDK, se le solicitará una barra de información resaltada sobre el Explorador de soluciones. Debe tener un aspecto similar al siguiente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalación del SDK de Visual Studio desde la línea de comandos  
 Puede instalar VSSDK desde la línea de comandos mediante el modificador **/InstallSelectableItems** con el instalador de Visual Studio. Para obtener más información sobre el uso de parámetros de línea de comandos con el instalador, vea [instalar Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Aquí se muestra cómo instalar VSSDK en modo silencioso con el instalador de la comunidad de Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Tenga en cuenta que debe usar el instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si ha instalado Visual Studio Enterprise en el equipo, debe ejecutar el instalador de Visual Studio Enterprise (vs_enterprise.exe).
