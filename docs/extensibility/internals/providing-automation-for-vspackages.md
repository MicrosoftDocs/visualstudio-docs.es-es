---
title: Proporcionar automatización para VSPackages ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705950"
---
# <a name="providing-automation-for-vspackages"></a>Provisión de automatización de VSPackages
Hay dos formas principales de proporcionar automatización para los VSPackages: mediante la implementación de objetos específicos de VSPackage e mediante la implementación de objetos de automatización estándar. Generalmente, estos se utilizan juntos para extender el modelo de automatización del entorno.

## <a name="vspackage-specific-objects"></a>Objetos específicos de VSPackage
 Algunos lugares dentro del modelo de automatización requieren que proporcione objetos de automatización que son únicos para el VSPackage. Por ejemplo, los nuevos proyectos requieren objetos distintos que solo proporciona el VSPackage. Los nombres de estos objetos se introducen en `DTE` el registro y se obtienen mediante llamadas al objeto de entorno.

 Objetos específicos de VSPackage también se pueden obtener cuando un consumidor de automatización utiliza el objeto proporcionado a través de la Object propiedad de un objeto estándar. Por ejemplo, `Window` el objeto `Object` estándar tiene una `Windows.Object` propiedad, conocida comúnmente como la propiedad. Cuando los consumidores llaman a la `Window.Object` en una ventana implementada en el VSPackage, se devuelve un objeto de automatización específico de su propio diseño.

#### <a name="projects"></a>Proyectos
 VSPackages puede extender el modelo de automatización para nuevos tipos de proyecto a través de sus propios objetos específicos de VSPackage. El propósito principal de proporcionar nuevos objetos de automatización para <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> el <xref:VSLangProj80.VSProject2> VSPackage es diferenciar los objetos de proyecto únicos de un objeto o un objeto. Esta diferenciación es útil cuando desea proporcionar una manera de seleccionar o iterar el tipo de proyecto aparte de otros tipos de proyecto, en caso de que aparezcan en paralelo en una solución. Para obtener más información, vea [Exponer objetos](../../extensibility/internals/exposing-project-objects.md)de proyecto .

#### <a name="events"></a>Events
 La arquitectura de eventos del entorno ofrece otro lugar para anexar sus propios objetos específicos de VSPackage. Por ejemplo, al crear sus propios objetos de evento únicos, puede ampliar el modelo de eventos del entorno para los proyectos. Es posible que desee proporcionar sus propios eventos cuando se agrega un nuevo elemento a su propio tipo de proyecto. Para obtener más información, consulte [Exposición de eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Window (Objetos)
 Windows puede devolver un objeto de automatización específico de VSPackage al entorno cuando se llama. Implementar un objeto que se <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> deriva `IDispatch` de , o que entrega las propiedades, extendiendo el objeto de ventana en el que se encuentra. Por ejemplo, puede usar este enfoque para proporcionar automatización para un control incrustado en un marco de ventana. La semántica de este objeto y cualquier otro objeto que pueda extender son suyos para diseñar. Para obtener más información, consulte [Cómo: Proporcionar automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opciones en el menú Herramientas
 Puede crear páginas para ampliar el modelo de automatización Herramientas y Opciones mediante la implementación de páginas y la adición de información al registro para crear sus propias opciones. A continuación, se puede llamar a las páginas a través del modelo de objetos de entorno como cualquier otra página de opciones. Si el diseño de la característica que va a agregar al entorno a través de VSPackages requiere páginas de opciones, a continuación, debe agregar la compatibilidad con automatización también. Para obtener más información, consulte [Compatibilidad con automatización para páginas](../../extensibility/internals/automation-support-for-options-pages.md)de opciones .

## <a name="standard-automation-objects"></a>Objetos de automatización estándar
 Para ampliar la automatización de proyectos, también se `IDispatch`implementan objetos de automatización estándar (derivados de ) que están al lado de los otros objetos de proyecto e implementan métodos y propiedades estándar. Entre los ejemplos de objetos estándar se incluyen los `Projects` `Project`objetos de proyecto que se insertan en la jerarquía de soluciones, como , , `ProjectItem`y `ProjectItems`. Cada nuevo tipo de proyecto debe implementar estos objetos (y posiblemente otros dependiendo de la semántica del proyecto).

 En cierto sentido, estos objetos proporcionan la ventaja opuesta de los objetos de proyecto específicos de VSPackage. Los objetos de automatización estándar permiten que el proyecto se utilice de forma generalizada como cualquier otro proyecto que admita los mismos objetos. Por lo tanto, un complemento `Project` que `ProjectItem` se escribe en general y los objetos pueden funcionar con proyectos de cualquier tipo. Para obtener más información, vea [Modelado de proyectos](../../extensibility/internals/project-modeling.md).
