---
title: Provisión de automatización de VSPackages | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b72e1493e8ab00f3aa98f3a9bd8e1e1dd30201e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614342"
---
# <a name="providing-automation-for-vspackages"></a>Provisión de automatización de VSPackages
Hay dos formas principales para proporcionar automatización para los VSPackages: mediante la implementación de objetos específicos de VSPackage y mediante la implementación de objetos de automatización estándar. Por lo general, se utilizan conjuntamente para ampliar el modelo de automatización del entorno.

## <a name="vspackage-specific-objects"></a>Objetos específicos de VSPackage
 Ciertos lugares dentro del modelo de automatización requieren que proporcione objetos de automatización que son únicos para el VSPackage. Por ejemplo, los nuevos proyectos requieren distintos objetos que sólo el VSPackage proporciona. Los nombres de estos objetos entran en el registro y obtenidos a través de llamadas en el entorno `DTE` objeto.

 Objetos específicos de VSPackage también pueden obtenerse cuando un consumidor de automatización usa el objeto proporcionado a través de la propiedad de objeto de un objeto estándar. Por ejemplo, el estándar `Window` objeto tiene un `Object` propiedad, conocida comúnmente como el `Windows.Object` propiedad. Cuando llama los consumidores la `Window.Object` en una ventana que se implementa en el paquete de VS, devolver un objeto de automatización específico de su propio diseño.

#### <a name="projects"></a>Proyectos
 Los paquetes VSPackage pueden extender el modelo de automatización para nuevos tipos de proyecto a través de sus propios objetos específicos de VSPackage. El propósito principal de proporcionar los nuevos objetos de automatización para el VSPackage es diferenciar el único proyecto objetos desde una <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o un <xref:VSLangProj80.VSProject2> objeto. Esta diferencia resulta útil cuando desea proporcionar una manera única o recorrer en iteración el tipo de proyecto, además de otros tipos de proyecto, debe aparecen en paralelo en una solución. Para obtener más información, consulte [exponer objetos del proyecto](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Eventos
 La arquitectura de eventos del entorno ofrece otro lugar para anexar sus propios objetos específicos de VSPackage. Por ejemplo, al crear sus propios objetos de evento único, puede ampliar el modelo de eventos del entorno para los proyectos. Es posible que desee proporcionar sus propios eventos cuando se agrega un nuevo elemento a su propio tipo de proyecto. Para obtener más información, consulte [exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Window (Objetos)
 Windows pueden devolver un objeto de automatización específico de VSPackage hasta que el entorno cuando se llama. Implementar un objeto que se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> o `IDispatch` que entrega volver propiedades, extender el objeto de ventana en la que está asociada. Por ejemplo, puede usar este enfoque para proporcionar automatización para un control situado en un marco de ventana. La semántica de este objeto y cualquier otro objeto que puede ampliar es suyos para diseñar. Para obtener más información, vea [Cómo: Provisión de automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opciones en el menú Herramientas
 Puede crear páginas para extender las herramientas, el modelo de automatización de opciones mediante la implementación de páginas y agregar información al registro para crear sus propias opciones. Las páginas, a continuación, se pueden llamar mediante el modelo de objetos de entorno como cualquier otras páginas de opciones. Si el diseño de la característica que se va a agregar al entorno a través de VSPackages requiere que las páginas de opciones, a continuación, debe agregar también la compatibilidad de automatización. Para obtener más información, consulte [compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Objetos de automatización estándar
 Para ampliar la automatización de proyectos, también se implementan los objetos de automatización estándar (derivado de `IDispatch`) que representan junto a los demás objetos del proyecto e implementar métodos y propiedades estándar. Ejemplos de objetos estándar de los objetos del proyecto que se insertan en la jerarquía de la solución como `Projects`, `Project`, `ProjectItem`, y `ProjectItems`. Estos objetos (y posiblemente otros registros según la semántica del proyecto), debe implementar cada nuevo tipo de proyecto.

 En cierto sentido, estos objetos proporcionan la ventaja de los objetos de proyecto específico de VSPackage opuesta. Los objetos de automatización estándar que el proyecto que se usará de forma generalizada como cualquier otro proyecto que admiten los mismos objetos. Por lo tanto, un complemento que se escribe en general `Project` y `ProjectItem` objetos pueden funcionar con proyectos de cualquier tipo. Para obtener más información, consulte [proyecto de modelado](../../extensibility/internals/project-modeling.md).