---
title: Instalar el SDK de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Instalar el SDK de Visual Studio
A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar el SDK de Visual Studio como parte de una instalación de Visual Studio  
 Si desea incluir el VSSDK en la instalación de Visual Studio, debe realizar una instalación personalizada.  
  
> [!NOTE]
>  En el archivo ejecutable de instalación, se llama el SDK de Visual Studio **herramientas de extensibilidad de Visual Studio**.  
  
1.  Inicie la instalación de Visual Studio 2015. Puede instalar cualquier edición de Visual Studio excepto Express.  
  
2.  En la primera pantalla, seleccione **personalizado**, no **predeterminado**. Haga clic en **Siguiente**.  
  
3.  Debería ver una vista de árbol de características personalizadas. Abra **herramientas comunes**. Debería ver **herramientas de extensibilidad de Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Comprobar **herramientas de extensibilidad de Visual Studio** , a continuación, haga clic en **siguiente** y continuar la instalación.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalar el SDK de Visual Studio después de instalar Visual Studio  
 Si decide instalar el SDK de Visual Studio después de completar la instalación de Visual Studio, debe seguir el procedimiento siguiente:  
  
1.  Vaya a **Panel de Control / programas / programas y características**y busque **Visual Studio 2015**. Puede instalar el SDK de Visual Studio para cualquier edición de Visual Studio 2015 excepto Express.  
  
2.  Haga clic en **Visual Studio 2015**y, a continuación, haga clic en **cambio**. Debería ver la página de instalación.  
  
3.  Siga el mismo procedimiento que en **instalar el SDK de Visual Studio como parte de una instalación de Visual Studio** anteriormente.  
  
4.  Haga clic en el **herramientas de extensibilidad de Visual Studio** vínculo para instalar el SDK de Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar el SDK de Visual Studio desde una solución  
 Si abre una solución con un proyecto de extensibilidad sin instalar primero el VSSDK, se le pedirá mediante una barra de información resaltada sobre el Explorador de soluciones. Debería ser similar al siguiente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar el SDK de Visual Studio desde la línea de comandos  
 Puede instalar la VSSDK desde la línea de comandos mediante la **/InstallSelectableItems** cambiar con el instalador de Visual Studio. Para obtener más información acerca de cómo utilizar parámetros de línea de comandos con el programa de instalación, consulte [utilizar parámetros de línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).  
  
 Aquí se muestra cómo instalar el VSSDK en modo silencioso utilizando al instalador de Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Tenga en cuenta que debe utilizar al instalador de Visual Studio que coincida con la versión instalada de Visual Studio. Por ejemplo, si tiene instalado en el equipo de Visual Studio Enterprise, debe ejecutar al instalador de Visual Studio Enterprise (vs_enterprise.exe).
