---
title: Compatibilidad de Automation con páginas de opciones | Microsoft Docs
description: Obtenga información sobre cómo hacer que las páginas de opciones de herramientas personalizadas de VSPackages estén disponibles para el Visual Studio de automatización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a4f6b33b7a5e17c610831db5d4387065915ea00
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901661"
---
# <a name="automation-support-for-options-pages"></a>Compatibilidad de Automation con páginas de opciones
Los VSPackages pueden proporcionar cuadros  de **diálogo Opciones** personalizados al menú Herramientas **(páginas** Opciones de herramientas) de y pueden hacer que estén disponibles para el modelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de automatización.

## <a name="tools-options-pages"></a>Opciones de herramientas (páginas)
 Para crear una **página Opciones de** herramientas, un VSPackage debe proporcionar una implementación de control de usuario devuelta al entorno a través de la implementación de VSPackage del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . (O bien, para el código administrado, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método ).

 Es opcional, pero muy recomendable, permitir el acceso a esta nueva página a través del modelo de automatización. Para hacerlo, siga estos pasos:

1. Extienda el objeto a través de la implementación de un objeto <xref:EnvDTE._DTE.Properties%2A> derivado de IDispatch.

2. Devuelve una implementación del método (o para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> código administrado el método ) al objeto derivado de <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> IDispatch.

3. Cuando un consumidor de automatización llama al método en una página de propiedades option personalizada, el entorno usa el método para obtener la implementación de automatización de una página de <xref:EnvDTE._DTE.Properties%2A> opciones de herramientas  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> personalizada. 

4. A continuación, el objeto de automatización del VSPackage se usa para proporcionar cada <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A> .

   Para obtener un ejemplo de implementación de una página **de opciones de herramientas personalizadas,** vea Ejemplos de [VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>Consulta también
- [Exposición de objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)
