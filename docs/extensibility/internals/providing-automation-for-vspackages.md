---
title: Proporcionar automatización para VSPackages | Microsoft Docs
description: Obtenga información acerca de cómo proporcionar automatización para sus VSPackages implementando objetos específicos de VSPackage y implementando objetos de automatización estándar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f9a19b5e0e543052dad492ab319595c8ef76dfe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060957"
---
# <a name="providing-automation-for-vspackages"></a>Provisión de automatización de VSPackages
Hay dos formas principales de proporcionar automatización para los VSPackages: mediante la implementación de objetos específicos de VSPackage y la implementación de objetos de automatización estándar. Por lo general, se usan conjuntamente para ampliar el modelo de automatización del entorno.

## <a name="vspackage-specific-objects"></a>Objetos VSPackage-Specific
 Algunos lugares del modelo de automatización requieren que proporcione objetos de automatización que sean únicos para el VSPackage. Por ejemplo, los nuevos proyectos requieren objetos distintos que solo proporciona el VSPackage. Los nombres de estos objetos se escriben en el registro y se obtienen a través de llamadas al objeto de entorno `DTE` .

 Los objetos específicos de VSPackage también se pueden obtener cuando un consumidor de automatización utiliza el objeto proporcionado a través de la propiedad de objeto de un objeto estándar. Por ejemplo, el `Window` objeto estándar tiene una `Object` propiedad, conocida comúnmente como la `Windows.Object` propiedad. Cuando los consumidores llaman a `Window.Object` en una ventana implementada en el VSPackage, debe devolver un objeto de automatización específico de su propio diseño.

#### <a name="projects"></a>Proyectos
 Los VSPackages pueden extender el modelo de automatización para los nuevos tipos de proyecto a través de sus propios objetos específicos del VSPackage. El objetivo principal de proporcionar nuevos objetos de automatización para el VSPackage es diferenciar los objetos de proyecto únicos de un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> objeto o. Esta diferenciación resulta útil cuando se desea proporcionar una manera de desplazarse o recorrer el tipo de proyecto de forma independiente con respecto a otros tipos de proyecto, en caso de que aparezcan en paralelo en una solución. Para obtener más información, vea [exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Events
 La arquitectura de eventos del entorno ofrece otro lugar para que anexe sus propios objetos específicos del VSPackage. Por ejemplo, mediante la creación de sus propios objetos de evento únicos, puede extender el modelo de eventos del entorno para los proyectos de. Es posible que desee proporcionar sus propios eventos cuando se agregue un nuevo elemento a su propio tipo de proyecto. Para obtener más información, vea [exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Window (Objetos)
 Windows puede devolver un objeto de automatización específico de VSPackage al entorno cuando se llama. Implemente un objeto que se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> , <xref:EnvDTE.IExtensibleObject> o `IDispatch` que revierte las propiedades, extendiendo el objeto de ventana en el que se encuentra en el sitio. Por ejemplo, puede utilizar este enfoque para proporcionar automatización a un control que esté en un marco de ventana. La semántica de este objeto y cualquier otro objeto que pueda extender son suyos. Para obtener más información, consulte [Cómo: proporcionar automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opciones en el menú herramientas
 Puede crear páginas para extender las herramientas, el modelo de automatización de opciones a través de la implementación de páginas y la adición de información al registro para crear sus propias opciones. A continuación, se puede llamar a las páginas a través del modelo de objetos de entorno como cualquier otra página de opciones. Si el diseño de la característica que va a agregar al entorno a través de VSPackages requiere páginas de opciones, debe agregar también la compatibilidad con la automatización. Para obtener más información, vea [compatibilidad de automatización con las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Objetos de automatización estándar
 Para extender la automatización de los proyectos, también implementa objetos de automatización estándar (derivados de `IDispatch` ) que se encuentran junto a los demás objetos de proyecto e implementan métodos y propiedades estándar. Entre los ejemplos de objetos estándar se incluyen los objetos de proyecto que se insertan en la jerarquía de la solución, como `Projects` , `Project` , `ProjectItem` y `ProjectItems` . Cada nuevo tipo de proyecto debe implementar estos objetos (y posiblemente otros, en función de la semántica del proyecto).

 En cierto sentido, estos objetos proporcionan la ventaja contraria de los objetos de proyecto específicos de VSPackage. Los objetos de automatización estándar permiten usar el proyecto de forma generalizada como cualquier otro proyecto que admita los mismos objetos. Por lo tanto, un complemento que se escribe en general `Project` y `ProjectItem` los objetos pueden funcionar en proyectos de cualquier tipo. Para obtener más información, vea [modelado del proyecto](../../extensibility/internals/project-modeling.md).
