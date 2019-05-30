---
title: Compatibilidad de automatización para las páginas de opciones | Microsoft Docs
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
ms.openlocfilehash: 0bf997205979cdfbb9c9f03492a5943f458e2d9c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342260"
---
# <a name="automation-support-for-options-pages"></a>Automatización de la compatibilidad con páginas de opciones
Los paquetes VSPackage pueden proporcionar una personalizada **opciones** cuadros de diálogo para la **herramientas** menú (**opciones de herramientas** páginas) en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y puede que estén disponibles para la automatización modelo.

## <a name="tools-options-pages"></a>Opciones de herramientas (páginas)
 Para crear un **herramientas-opciones** página, un VSPackage debe proporcionar una implementación de control de usuario devuelta en el entorno a través de la implementación de VSPackage el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método. (O, para código administrado, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método.)

 Es opcional, pero se recomienda encarecidamente, para permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo con los pasos siguientes:

1. Ampliar la <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.

2. Devolver una implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método (o para código administrado la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> método) para el objeto derivado de IDispatch.

3. Cuando un consumidor de automatización llama a la <xref:EnvDTE._DTE.Properties%2A> método en un personalizado **opción** página de propiedades, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener un personalizado **herramientas-opciones** automatización de la página implementación de.

4. El objeto de automatización de VSPackage, a continuación, se usa para proporcionar cada <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A>.

   Para obtener un ejemplo de implementación personalizado **herramientas-opciones** página, vea [muestras de VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>Vea también
- [Exponer objetos del proyecto](../../extensibility/internals/exposing-project-objects.md)