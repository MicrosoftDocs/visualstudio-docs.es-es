---
title: Filtrar Implementar la buscar y reemplazar el mecanismo | Microsoft Docs
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
ms.openlocfilehash: a42df69a7c51b7eb7ef44cf137d8449cf1421ae2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997108"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Filtrar Implementar la buscar y reemplazar el mecanismo de
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona dos maneras de implementar la búsqueda y reemplazo. Una consiste en pasar de una imagen de texto en el shell y permitirle controlar la búsqueda, el resaltado y reemplazar texto. Esto permite a los usuarios especificar varios intervalos de texto. Como alternativa, el VSPackage puede controlar esta funcionalidad propia. En ambos casos debe notificar al shell sobre el destino actual y los destinos para todos los documentos abiertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar la búsqueda y reemplazo  
  
1.  Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaz en uno de los objetos devueltos por las propiedades de marco <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Si va a crear un editor personalizado, debe implementar esta interfaz como parte de la clase de editor personalizado.  
  
2.  Use el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar las opciones que admite el editor y para indicar si implementa la búsqueda de imágenes de texto.  
  
     Si el editor admite la búsqueda de imágenes de texto, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     En caso contrario, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Si implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> métodos, puede simplificar las tareas de búsqueda mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
