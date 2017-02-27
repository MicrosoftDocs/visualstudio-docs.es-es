---
title: "Idiomas contenidos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - contenidos idiomas"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Idiomas contenidos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Lenguajes contenidos* son lenguajes incluidos en otros lenguajes.  Por ejemplo, HTML en las páginas de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] puede contener [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o scripts de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  Una arquitectura de dual\-lenguaje es necesario para que el editor de archivos .aspx proporciona IntelliSense, el color, y otras características de edición de HTML y el lenguaje de scripting.  
  
## Implementación  
 La interfaz más importante que necesita implementar para lenguajes contenidos es la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Esta interfaz se implementa mediante cualquier lenguaje que se puede hospedar en un lenguaje primario.  Proporciona acceso al colorizer del servicio de lenguaje, el filtro de la vista de texto, y a la identificación primaria del servicio de lenguaje  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> permite crear una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Los pasos siguientes muestran cómo implementar un lenguaje contenido:  
  
1.  Utilice `QueryService()` para obtener el identificador del servicio de lenguaje y el identificador de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> para crear una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  pase una interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , un Id. de elemento \(uno o más de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, o de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) y una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .  
  
3.  La interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> , que es el objeto coordinador del búfer de texto, proporciona servicios básicos necesarios para asignar ubicaciones en un archivo principal en el búfer de lenguaje secundario.  
  
     Por ejemplo, en un único archivo .aspx, el archivo principal incluye ASP, HTML y todo el código se contiene que.  Sin embargo, el búfer secundario, contiene solo el código contenido, así como cualquier definición de clase, para hacer el búfer secundario en un archivo de código válido.  El coordinador de búfer controla el trabajo de ediciones de coordinación a partir de un búfer al otro.  
  
4.  El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> , que es el idioma principal, indica al coordinador de búfer qué texto dentro del búfer se asigna al texto correspondiente en el búfer secundario.  
  
     El lenguaje pasa una matriz de la estructura de <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> , que actualmente sólo un intervalo primaria y secundaria.  
  
5.  El método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> y el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> proporcionan la asignación al búfer secundario y viceversa de primario.