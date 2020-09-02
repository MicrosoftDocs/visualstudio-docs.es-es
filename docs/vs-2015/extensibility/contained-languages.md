---
title: Idiomas contenidos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184282"
---
# <a name="contained-languages"></a>Lenguajes incluidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

Los *idiomas contenidos* son idiomas incluidos en otros lenguajes. Por ejemplo, HTML en [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] páginas puede contener [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] scripts o. Se necesita una arquitectura de dos idiomas para que el editor de archivos. aspx proporcione IntelliSense, coloración y otras características de edición para HTML y para el lenguaje de scripting.  
  
## <a name="implementation"></a>Implementación  
 La interfaz más importante que debe implementar para los lenguajes contenidos es la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Esta interfaz se implementa mediante cualquier lenguaje que se pueda hospedar dentro de un lenguaje principal. Proporciona acceso al coloreador del servicio de lenguaje, al filtro de la vista de texto y al identificador del servicio de lenguaje principal. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Permite crear una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. En los pasos siguientes se muestra cómo implementar un lenguaje contenido:  
  
1. Utilice `QueryService()` para obtener el identificador del servicio de lenguaje y el identificador de interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método para crear una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Pase una <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz, uno o varios [identificadores de elemento](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) y una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz.  
  
3. La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz, que es el objeto Coordinador de búfer de texto, proporciona los servicios básicos necesarios para asignar las ubicaciones de un archivo principal en el búfer del lenguaje secundario.  
  
     Por ejemplo, en un único archivo. aspx, el archivo principal incluye ASP, HTML y todo el código que contiene. Sin embargo, el búfer secundario incluye solo el código contenido, junto con las definiciones de clase, para convertir el búfer secundario en un archivo de código válido. El Coordinador del búfer controla el trabajo de coordinar las ediciones de un búfer al otro.  
  
4. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que es el lenguaje principal, indica al Coordinador del búfer qué texto de su búfer se asigna al texto correspondiente en el búfer secundario.  
  
     El lenguaje pasa en una matriz de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estructura, que actualmente solo incluye un intervalo principal y otro secundario.  
  
5. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método proporcionan la asignación del búfer principal al secundario y viceversa.
