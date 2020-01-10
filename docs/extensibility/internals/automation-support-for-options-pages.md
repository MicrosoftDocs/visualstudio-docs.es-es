---
title: Compatibilidad de automatización con las páginas de opciones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848965"
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de automatización con las páginas de opciones
Los paquetes VSPackage pueden proporcionar cuadros de diálogo de **Opciones** personalizadas al menú **herramientas** (páginas**opciones de herramientas** ) en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y pueden hacer que estén disponibles para el modelo de automatización.

## <a name="tools-options-pages"></a>Opciones de herramientas (páginas)
 Para crear una página de **Opciones de herramientas** , un VSPackage debe proporcionar una implementación de control de usuario devuelta al entorno a través de la implementación del VSPackage del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. (O, en el caso del código administrado, el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>).

 Es opcional, pero se recomienda encarecidamente, permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo con los siguientes pasos:

1. Extienda el objeto <xref:EnvDTE._DTE.Properties%2A> a través de la implementación de un objeto derivado de IDispatch.

2. Devuelve una implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (o de código administrado el método <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) al objeto derivado de IDispatch.

3. Cuando un consumidor de automatización llama al método <xref:EnvDTE._DTE.Properties%2A> en una página de propiedades de **opción** personalizada, el entorno usa el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> para obtener una implementación de automatización de la página **Opciones de herramientas** personalizadas.

4. A continuación, se usa el objeto de automatización del VSPackage para proporcionar cada <xref:EnvDTE.Property> devuelta por <xref:EnvDTE._DTE.Properties%2A>.

   Para obtener un ejemplo de implementación de una página de **Opciones de herramientas** personalizadas, vea [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vea también
- [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)
