---
title: "Proporciona la automatización para VSPackages | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 63912603a888f3d2c45b8b08a7aba93af0694ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-vspackages"></a>Proporciona la automatización para VSPackages
Hay dos formas principales para proporcionar la automatización para los VSPackages: mediante la implementación de objetos específicos de VSPackage y mediante la implementación de objetos de automatización estándar. Por lo general, estos se utilizan en juntos para ampliar el modelo de automatización del entorno.  
  
## <a name="vspackage-specific-objects"></a>Objetos específicos de VSPackage  
 Ciertos lugares dentro del modelo de automatización requieren que proporcione los objetos de automatización que son únicos para el VSPackage. Por ejemplo, nuevos proyectos requieren distintos objetos que proporciona solo el VSPackage. Los nombres de estos objetos están escritos en el registro y se obtienen a través de llamadas en el entorno de `DTE` objeto.  
  
 También se pueden obtener objetos específicos de VSPackage cuando un consumidor de automatización usa el objeto proporcionado a través de la propiedad de objeto de un objeto estándar. Por ejemplo, el estándar `Window` objeto tiene una `Object` propiedad, que se conoce normalmente como el `Windows.Object` propiedad. Cuando llama los consumidores la `Window.Object` en una ventana que se implementa en el paquete de VS, se vuelva a pasar un objeto de automatización específico de su propio diseño.  
  
#### <a name="projects"></a>Proyectos  
 Paquetes VSPackage puede extender el modelo de automatización para nuevos tipos de proyecto a través de sus propios objetos específicos de VSPackage. El propósito principal de proporcionar los nuevos objetos de automatización para el VSPackage es diferenciar el proyecto único objetos desde una <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o un <xref:VSLangProj80.VSProject2> objeto. Esta diferencia resulta útil cuando desea proporcionar una manera para escoger o recorrer en iteración el tipo de proyecto además de otros tipos de proyecto, debe aparecen en paralelo en una solución. Para obtener más información, consulte [exponer objetos del proyecto](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Eventos  
 La arquitectura de eventos del entorno ofrece otro lugar para anexar sus propios objetos específicos de VSPackage. Por ejemplo, mediante la creación de sus propios objetos de evento único, puede ampliar el modelo de evento del entorno para los proyectos. Puede proporcionar sus propios eventos cuando se agrega un nuevo elemento a su propio tipo de proyecto. Para obtener más información, consulte [exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Window (Objetos)  
 Windows puede devolver un objeto de automatización de VSPackage específicos hacia el entorno cuando se llama. Implementar un objeto que se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> o `IDispatch` que entrega vuelve propiedades, extender el objeto de ventana en la que está asociada. Por ejemplo, puede usar este método para proporcionar la automatización para un control ubicado en un marco de ventana. La semántica de este objeto y cualquier otro objeto que puede ampliar el quedan a su diseño. Para obtener más información, consulte [Cómo: proporcionar automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Páginas de opciones en el menú Herramientas  
 Puede crear páginas para extender las herramientas, el modelo de automatización de opciones mediante la implementación de páginas y agregando la información en el registro para crear sus propias opciones. A continuación, pueden llamar a las páginas mediante el modelo de objetos de entorno como cualquier otras páginas de opciones. Si el diseño de la característica que se va a agregar al entorno a través de VSPackages requiere que las páginas de opciones, debe agregar la compatibilidad de la automatización. Para obtener más información, consulte [compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Objetos de automatización estándar  
 Para extender la automatización para los proyectos, también se implementan objetos de automatización estándar (derivado de `IDispatch`) que representan junto a los demás objetos de proyecto e implementar propiedades y métodos estándar. Algunos ejemplos de objetos estándar son los objetos del proyecto que se insertan en la jerarquía de la solución como `Projects`, `Project`, `ProjectItem`, y `ProjectItems`. Estos objetos (y posiblemente otros unos según la semántica del proyecto), debe implementar cada nuevo tipo de proyecto.  
  
 En un sentido, estos objetos proporcionan la ventaja de los objetos de proyecto específicos del VSPackage opuesta. Los objetos de automatización estándar permiten el proyecto que se usará de forma generalizada como cualquier otro proyecto compatible con los mismos objetos. Por lo tanto, un complemento que se escribe en general `Project` y `ProjectItem` objetos pueden funcionar en proyectos de cualquier tipo. Para obtener más información, consulte [proyecto de modelado](../../extensibility/internals/project-modeling.md).