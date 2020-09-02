---
title: 'Cómo: implementar el mecanismo de búsqueda y reemplazo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548703"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Cómo: Implementar el mecanismo Buscar y reemplazar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona dos maneras de implementar buscar y reemplazar. Una manera es pasar una imagen de texto al shell y permitir que administre la búsqueda, el resaltado y el reemplazo de texto. Esto permite a los usuarios especificar varios intervalos de texto. Como alternativa, el VSPackage puede controlar esta funcionalidad. En ambos casos, debe notificar al shell el destino actual y los destinos de todos los documentos abiertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar buscar y reemplazar  
  
1. Implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaz en uno de los objetos devueltos por las propiedades de marco <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Si está creando un editor personalizado, debe implementar esta interfaz como parte de la clase personalizada del editor.  
  
2. Use el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar las opciones que admite el editor e indicar si implementa la búsqueda de imágenes de texto.  
  
     Si el editor admite la búsqueda de imágenes de texto, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     De lo contrario, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. Si implementa los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> métodos y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> , puede simplificar las tareas de búsqueda llamando a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaz.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
