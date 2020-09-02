---
title: Compatibilidad de automatización con las páginas de opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157246"
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de automatización con páginas de opciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los paquetes VSPackage pueden proporcionar cuadros de diálogo de **Opciones** personalizadas al menú **herramientas** (páginas opciones de herramientas) en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y pueden hacer que estén disponibles para el modelo de automatización.  
  
## <a name="tools-options-pages"></a>Páginas de opciones de herramientas  
 Para crear una página de **Opciones de herramientas** , un VSPackage debe proporcionar una implementación de control de usuario devuelta al entorno a través de la implementación del VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método (o para el método de código administrado <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> ).  
  
 Es opcional, pero se recomienda encarecidamente, permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo a través de los pasos siguientes:  
  
1. Extienda el <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.  
  
2. Devuelve una implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o de código administrado el <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) al objeto derivado de IDispatch.  
  
3. Cuando un consumidor de automatización llama al <xref:EnvDTE._DTE.Properties%2A> método en una página de propiedades de **opción** personalizada, el entorno usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener la implementación de automatización de una página de **Opciones de herramientas** personalizada.  
  
4. A continuación, se usa el objeto de automatización del VSPackage para proporcionar cada <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A> .  
  
   Para obtener un ejemplo de implementación de una página de opciones de herramientas personalizadas, vea [ejemplos de VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Consulte también  
 [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)
