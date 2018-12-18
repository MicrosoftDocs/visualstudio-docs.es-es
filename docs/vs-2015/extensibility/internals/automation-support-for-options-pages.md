---
title: Compatibilidad de automatización para las páginas de opciones | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6205d01547f7243234facfb43db80303c9b71c51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720261"
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de automatización con páginas de opciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los paquetes VSPackage pueden proporcionar una personalizada **opciones** cuadros de diálogo para la **herramientas** menú (páginas de opciones de herramientas) en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y puede que estén disponibles en el modelo de automatización.  
  
## <a name="tools-options-pages"></a>Páginas de opciones de herramientas  
 Para crear un **herramientas-opciones** página, un VSPackage debe proporcionar una implementación de control de usuario devuelta en el entorno a través de la implementación de VSPackage el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método (o código administrado la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método).  
  
 Es opcional, pero se recomienda encarecidamente, para permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo a través de los pasos siguientes:  
  
1. Ampliar la <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.  
  
2. Devolver una implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o para código administrado la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) para el objeto derivado de IDispatch.  
  
3. Cuando un consumidor de automatización llama a la <xref:EnvDTE._DTE.Properties%2A> método en un personalizado **opción** página de propiedades, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener un personalizado **herramientas-opciones** automatización de la página implementación de.  
  
4. El objeto de automatización de VSPackage, a continuación, se usa para proporcionar cada <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A>.  
  
   Para obtener un ejemplo de implementación de una página de opciones de herramientas personalizada, consulte [muestras de VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)

