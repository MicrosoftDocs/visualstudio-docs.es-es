---
title: Contenido idiomas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bfdbc3d1c0e7bbc0b3dc712d9434ca1b49c6feca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="contained-languages"></a>Idiomas independientes
*Contenido idiomas* idiomas incluidos en otros lenguajes. Por ejemplo, HTML en [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] páginas pueden contener [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] las secuencias de comandos. Una arquitectura de doble idioma es necesaria para el editor de archivos .aspx proporcionar IntelliSense, la coloración y otras características de edición para el código HTML y el lenguaje de scripting.  
  
## <a name="implementation"></a>Implementación  
 La interfaz más importante que debe implementar para idiomas independientes es el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Esta interfaz se implementa mediante cualquier lenguaje que se puede hospedar dentro de un idioma principal. Proporciona acceso para el servicio de lenguaje aplicador de color, filtro de la vista de texto e Id. de servicio de idioma principal. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> le permite crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Los pasos siguientes muestran cómo implementar un lenguaje independiente:  
  
1.  Use `QueryService()` para obtener el idioma de Id. de servicio y el identificador de interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método para crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Pasar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz, un identificador de elemento (uno o más de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, o <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz.  
  
3.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz, que es el objeto de coordinador de búfer de texto, proporciona los servicios básicos que deben asignar ubicaciones en un archivo principal en búfer del idioma secundario.  
  
     Por ejemplo, en un archivo .aspx único, el archivo principal incluye la ASP, HTML y todo el código que se encuentra. Sin embargo, el búfer secundario, incluye sólo el código independiente, junto con las definiciones de clase, para crear el búfer secundario en un archivo de código válido. El Coordinador de búfer administra el trabajo de coordinar todas las modificaciones de un búfer a otro.  
  
4.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que es el idioma principal, indica que el coordinador del búfer se asigna el texto dentro de su búfer a texto correspondiente en el búfer secundario.  
  
     El idioma que se pasa en una matriz de los <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estructura, que actualmente solo incluye un elemento principal y un intervalo secundario.  
  
5.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método proporciona la asignación del objeto principal al búfer secundario y viceversa.