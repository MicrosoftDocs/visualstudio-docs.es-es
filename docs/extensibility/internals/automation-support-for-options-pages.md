---
title: Soporte de automatización para las páginas de opciones de la aplicación de la aplicación de la aplicación de Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709933"
---
# <a name="automation-support-for-options-pages"></a>Soporte de automatización para páginas de opciones
VSPackages puede proporcionar **opciones** personalizadas cuadros de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para el **herramientas** menú **(páginas** de opciones de herramientas) en y puede ponerlos a disposición del modelo de automatización.

## <a name="tools-options-pages"></a>Opciones de herramientas (páginas)
 Para crear un **opciones** de herramientas página, un VSPackage debe proporcionar una implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> de control de usuario devuelto al entorno a través de la implementación de VSPackage del método. (O, para el código <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> administrado, el método.)

 Es opcional, pero muy recomendable, permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo con los siguientes pasos:

1. Extienda <xref:EnvDTE._DTE.Properties%2A> el objeto a través de la implementación de un IDispatch-objeto derivado.

2. Devuelve una implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o para el código administrado el <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) al objeto derivado de IDispatch.

3. Cuando un consumidor <xref:EnvDTE._DTE.Properties%2A> de automatización llama al método en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> una página de propiedades **Option** personalizada, el entorno usa el método para obtener la implementación de automatización de una página **Opciones** de herramientas personalizada.

4. A continuación, se usa el objeto <xref:EnvDTE.Property> de <xref:EnvDTE._DTE.Properties%2A>automatización del VSPackage para proporcionar cada uno devuelto por .

   Para obtener un ejemplo de implementación de una página **de opciones** de herramientas personalizadas, vea [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vea también
- [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)
