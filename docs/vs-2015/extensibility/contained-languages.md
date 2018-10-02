---
title: Contenidos de lenguajes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0b455a526bf1b32de90588a103c23855e730946
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579435"
---
# <a name="contained-languages"></a>Lenguajes contenidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

La versión más reciente de este tema puede encontrarse en [lenguajes contenidos](https://docs.microsoft.com/visualstudio/extensibility/contained-languages).  
  
*Contenidos de lenguajes* son lenguajes contenidos en otros lenguajes. Por ejemplo, HTML en [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] páginas pueden contener [!INCLUDE[csprcs](../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] secuencias de comandos. Una arquitectura de doble lenguaje es necesaria para el editor de archivos .aspx proporcionar IntelliSense, colores y otras características de edición para el código HTML y el lenguaje de scripting.  
  
## <a name="implementation"></a>Implementación  
 La interfaz más importante que debe implementar para los lenguajes contenidos es la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Esta interfaz se implementa mediante cualquier lenguaje que se puede hospedar dentro de un idioma principal. Proporciona acceso a Coloreador del servicio de lenguaje, filtro de vista de texto e Id. de servicio de idioma principal. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> le permite crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Los pasos siguientes muestran cómo implementar un lenguaje contenido:  
  
1.  Use `QueryService()` para obtener el idioma de Id. de servicio y el identificador de interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método para crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Pasar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz, uno o varios [identificadores de elemento](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz.  
  
3.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz, que es el objeto de coordinador del búfer de texto, proporciona los servicios básicos que se necesitan para asignar ubicaciones en un archivo principal en el búfer del lenguaje secundario.  
  
     Por ejemplo, en un solo archivo .aspx, el archivo principal incluye el ASP, HTML y todo el código que se encuentra. Sin embargo, el búfer secundario, incluye sólo el código independiente, junto con las definiciones de clase, para hacer que el búfer secundario de un archivo de código válido. El Coordinador de búfer controla el trabajo de coordinación de las ediciones de un búfer a otro.  
  
4.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que es el idioma principal, indica que el Coordinador de búfer dentro de su búfer de texto se asigna al texto correspondiente en el búfer secundario.  
  
     El idioma que se pasa en una matriz de los <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estructura, que actualmente solo incluye un elemento principal y un intervalo secundario.  
  
5.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método proporciona la asignación de principal a un búfer secundario y viceversa.

