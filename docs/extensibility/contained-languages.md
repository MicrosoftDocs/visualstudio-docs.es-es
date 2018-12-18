---
title: Contenidos de lenguajes | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edaed1eef81d493bdd29311893caef93447e6f7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231749"
---
# <a name="contained-languages"></a>Lenguajes contenidos

*Contenidos de lenguajes* son lenguajes contenidos en otros lenguajes. Por ejemplo, HTML en [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] páginas pueden contener [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] secuencias de comandos. Es necesaria para una arquitectura de doble lenguaje el *.aspx* editor de archivos para proporcionar IntelliSense, colores y edición de otras características para el código HTML y el lenguaje de scripting.

## <a name="implementation"></a>Implementación

La interfaz más importante que debe implementar para los lenguajes contenidos es la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Esta interfaz se implementa mediante cualquier lenguaje que se puede hospedar dentro de un idioma principal. Proporciona acceso a Coloreador del servicio de lenguaje, filtro de vista de texto e Id. de servicio de idioma principal. El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> le permite crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz. Los pasos siguientes muestran cómo implementar un lenguaje contenido:

1.  Use `QueryService()` para obtener el idioma de Id. de servicio y el identificador de interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Para crear un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfaz, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método. Pasar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz, uno o varios [identificadores de elemento](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz.

3.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfaz, que es el objeto de coordinador del búfer de texto, proporciona los servicios básicos que se necesitan para asignar ubicaciones en un archivo principal en el búfer del lenguaje secundario.

     Por ejemplo, en una sola *.aspx* archivo, el archivo principal incluye el ASP, HTML y todo el código que se encuentra. Sin embargo, el búfer secundario incluye sólo el código incluido junto con las definiciones de clase, para hacer que el búfer secundario de un archivo de código válido. El Coordinador de búfer controla el trabajo de coordinación de las ediciones de un búfer a otro.

4.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que es el idioma principal, indica que el Coordinador de búfer dentro de su búfer de texto se asigna al texto correspondiente en el búfer secundario.

     El idioma que se pasa en una matriz de los <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estructura, que actualmente solo incluye un elemento principal y un intervalo secundario.

5.  El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método y el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método proporciona la asignación de principal a un búfer secundario y viceversa.