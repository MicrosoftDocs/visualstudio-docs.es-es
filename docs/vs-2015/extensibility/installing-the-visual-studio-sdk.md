---
title: Instalar el SDK de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 796d5f3f233310157b0784e213b81237e767055b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997316"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar el SDK de Visual Studio como parte de una instalación de Visual Studio  
 Si desea incluir VSSDK en la instalación de Visual Studio, debe realizar una instalación personalizada.  
  
> [!NOTE]
>  En el ejecutable de instalación, el SDK de Visual Studio se denomina **herramientas de extensibilidad de Visual Studio**.  
  
1.  Inicie la instalación de Visual Studio 2015. Puede instalar cualquier edición de Visual Studio, excepto Express.  
  
2.  En la primera pantalla, seleccione **personalizado**, no **predeterminado**. Haga clic en **Siguiente**.  
  
3.  Debería ver una vista de árbol de características personalizadas. Abra **herramientas comunes**. Debería ver **herramientas de extensibilidad de Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Comprobar **herramientas de extensibilidad de Visual Studio** , a continuación, haga clic en **siguiente** y continuar con la instalación.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar el SDK de Visual Studio después de instalar Visual Studio  
 Si decide instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, debe seguir el procedimiento siguiente:  
  
1.  Vaya a **Panel de Control / programas o programas y características**y busque **Visual Studio 2015**. Puede instalar el SDK de Visual Studio para cualquier edición de Visual Studio 2015, excepto Express.  
  
2.  Haga clic en **Visual Studio 2015**y, a continuación, haga clic en **cambio**. Debería ver la página de instalación.  
  
3.  Siga el mismo procedimiento que en **instalar el SDK de Visual Studio como parte de una instalación de Visual Studio** anteriormente.  
  
4.  Haga clic en el **herramientas de extensibilidad de Visual Studio** vínculo para instalar el SDK de Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar el SDK de Visual Studio desde una solución  
 Si abre una solución sin instalar primero el VSSDK con un proyecto de extensibilidad, se le pedirá por una barra de información resaltado anteriormente el Explorador de soluciones. Debe tener un aspecto similar al siguiente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar el SDK de Visual Studio desde la línea de comandos  
 Puede instalar VSSDK desde la línea de comandos mediante la **/installselectableitems** cambie con el instalador de Visual Studio. Para obtener más información sobre cómo usar parámetros de línea de comandos con el programa de instalación, consulte [instalar Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Aquí le mostramos cómo instalar el VSSDK en modo silencioso mediante el instalador de Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Tenga en cuenta que debe usar al instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene Visual Studio Enterprise instalado en el equipo, debe ejecutar al instalador de Visual Studio Enterprise (vs_enterprise.exe).
