---
title: Compatibilidad de automatización con las páginas de opciones | Microsoft Docs
description: Obtenga información sobre cómo hacer que las páginas de opciones de herramientas personalizadas en VSPackages estén disponibles para el modelo de automatización de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 532568dc0e4d181dfe3de56151096565bf9ff771
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905978"
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de automatización con las páginas de opciones
Los paquetes VSPackage pueden proporcionar cuadros de diálogo de **Opciones** personalizadas al menú **herramientas** (páginas **Opciones de herramientas** ) en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y pueden hacer que estén disponibles para el modelo de automatización.

## <a name="tools-options-pages"></a>Opciones de herramientas (páginas)
 Para crear una página de **Opciones de herramientas** , un VSPackage debe proporcionar una implementación de control de usuario devuelta al entorno a través de la implementación del VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método. (O, en el caso del código administrado, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método).

 Es opcional, pero se recomienda encarecidamente, permitir el acceso a esta nueva página a través del modelo de automatización. Para hacerlo, siga estos pasos:

1. Extienda el <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.

2. Devuelve una implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o de código administrado el <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) al objeto derivado de IDispatch.

3. Cuando un consumidor de automatización llama al <xref:EnvDTE._DTE.Properties%2A> método en una página de propiedades de **opción** personalizada, el entorno usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener la implementación de automatización de una página de **Opciones de herramientas** personalizada.

4. A continuación, se usa el objeto de automatización del VSPackage para proporcionar cada <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A> .

   Para obtener un ejemplo de implementación de una página de **Opciones de herramientas** personalizadas, vea [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vea también
- [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)
