---
title: "Automatizaci&#243;n de VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, automatización [Visual Studio SDK]"
  - "automatización [Visual Studio SDK] VSPackages"
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Automatizaci&#243;n de VSPackages
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Hay dos formas principales para proporcionar automatización para los VSPackages: mediante la implementación de objetos específicos de VSPackage y mediante la implementación de objetos de automatización estándar. Por lo general, estos se utilizan en juntos para ampliar el modelo de automatización del entorno.  
  
## Objetos específicos de VSPackage  
 Determinados lugares dentro del modelo de automatización requieren que se proporcionan los objetos de automatización que son únicos para el VSPackage. Por ejemplo, nuevos proyectos requieren distintos objetos que proporciona solo el VSPackage. Los nombres de estos objetos están escritos en el registro y obtenidos a través de llamadas en el entorno de `DTE` objeto.  
  
 También se pueden obtener objetos específicos de VSPackage cuando un consumidor de automatización utiliza el objeto proporcionado a través de la propiedad de objeto de un objeto estándar. Por ejemplo, el estándar `Window` objeto tiene una `Object` propiedad, conocido comúnmente como el `Windows.Object` propiedad. Cuando llama los consumidores de la `Window.Object` en una ventana de implementada en su VSPackage, vuelva a pasar un objeto de automatización específico de su propio diseño.  
  
#### Proyectos  
 VSPackages pueden ampliar el modelo de automatización para los nuevos tipos de proyecto a través de sus propios objetos específicos de VSPackage. El propósito principal de proporcionar nuevos objetos de automatización para el VSPackage es diferenciar el único proyecto objetos desde un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o un <xref:VSLangProj80.VSProject2> objeto. Esta diferencia resulta útil cuando desea proporcionar una manera de escoger o recorrer en iteración el tipo de proyecto, además de otros tipos de proyecto, debería aparecen en paralelo en una solución. Para obtener más información, consulta [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md).  
  
#### Eventos  
 La arquitectura de eventos del entorno ofrece otro lugar para agregar sus propios objetos específicos de VSPackage. Por ejemplo, mediante la creación de sus propios objetos de evento único, puede ampliar el modelo de eventos del entorno para proyectos. Desea proporcionar sus propios eventos cuando se agrega un nuevo elemento a su propio tipo de proyecto. Para obtener más información, consulta [Exponer eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### Window \(Objetos\)  
 Windows puede devolver un objeto de automatización específico de VSPackage vuelva al entorno cuando se llama. Implementar un objeto que se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> o `IDispatch` que da vuelta propiedades, extender el objeto de ventana en la que está asociada. Por ejemplo, puede utilizar este método para proporcionar automatización para un control ubicado en un marco de ventana. La semántica de este objeto y cualquier otro objeto que puede extender quedan a su diseño. Para obtener más información, consulta [Cómo: proporcionar automatización para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### Páginas de opciones en el menú Herramientas  
 Puede crear páginas para extender las herramientas, el modelo de automatización de opciones mediante la implementación de páginas y agregar información al registro para crear sus propias opciones. A continuación, pueden llamar a las páginas mediante el modelo de objetos de entorno como las otras páginas de opciones. Si el diseño de la característica que se va a agregar al entorno a través de VSPackages requiere que las páginas de opciones, debe agregar también la compatibilidad con la automatización. Para obtener más información, consulta [Compatibilidad de automatización para las páginas de opciones](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## Objetos de automatización estándar  
 Para extender la automatización de proyectos, también se implementan objetos de automatización estándar \(derivado de `IDispatch`\) que representan junto a los objetos del proyecto e implementar propiedades y métodos estándar. Ejemplos de objetos estándar, los objetos del proyecto que se insertan en la jerarquía de la solución como `Projects`, `Project`, `ProjectItem`, y `ProjectItems`. Estos objetos \(y posiblemente otros unos según la semántica del proyecto\), debe implementar cada nuevo tipo de proyecto.  
  
 En cierto sentido, estos objetos proporcionan la ventaja de los objetos de proyecto específicos de VSPackage opuesta. Los objetos de automatización estándar permiten el proyecto que se usará de forma generalizada como cualquier otro proyecto compatible con los mismos objetos. Por lo tanto, un complemento que se escribe en general `Project` y `ProjectItem` objetos pueden funcionar con proyectos de cualquier tipo. Para obtener más información, consulta [Modelo de proyecto](../../extensibility/internals/project-modeling.md).