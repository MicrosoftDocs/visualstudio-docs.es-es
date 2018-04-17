---
title: Compatibilidad de automatización para las páginas de opciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de automatización para las páginas de opciones
VSPackages puede proporcionar personalizado **opciones** cuadros de diálogo para la **herramientas** menú (páginas de opciones de herramientas) en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y puede que estén disponibles en el modelo de automatización.  
  
## <a name="tools-options-pages"></a>Páginas de opciones de herramientas  
 Para crear un **opciones de herramientas** página, un VSPackage debe proporcionar una implementación de control de usuario devuelta en el entorno a través de la implementación de VSPackage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método (o código administrado la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método).  
  
 Es opcional, pero se recomienda encarecidamente, para permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo a través de los pasos siguientes:  
  
1.  Ampliar la <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.  
  
2.  Devuelva una implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o para el código administrado la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) para el objeto derivado de IDispatch.  
  
3.  Cuando un consumidor de automatización llama el <xref:EnvDTE._DTE.Properties%2A> método en un personalizado **opción** usa el entorno de página de propiedades, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener un personalizado **opciones de herramientas** automatización de la página implementación de.  
  
4.  El objeto de automatización de VSPackage, a continuación, se utiliza para proporcionar a cada uno de ellos <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A>.  
  
 Para obtener un ejemplo de implementación de una página de opciones de herramientas personalizada, vea [muestras de VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Vea también  
 [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)