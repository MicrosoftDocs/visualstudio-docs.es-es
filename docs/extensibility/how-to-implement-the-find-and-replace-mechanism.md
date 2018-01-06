---
title: "Cómo: implementar la buscar y reemplazar mecanismo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c971d4565c95cab23e683a1a4f20c75ebea81b8f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Cómo: implementar la buscar y reemplazar el mecanismo de
Visual Studio proporciona dos maneras de implementar la búsqueda y reemplazo. Una manera es pasar una imagen de texto en el shell y que controle la búsqueda, el resaltado y reemplazar texto. Esto permite a los usuarios especificar varios intervalos de texto. O bien, el VSPackage puede controlar esta funcionalidad. En ambos casos debe notificar el shell sobre el destino actual y los destinos para todos los documentos abiertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar buscar y reemplazar  
  
1.  Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaz en uno de los objetos devueltos por las propiedades de marco <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Si va a crear un editor personalizado, debe implementar esta interfaz como parte de la clase de editor personalizado.  
  
2.  Use la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar las opciones que admite el editor y para indicar si implementa la búsqueda de imagen de texto.  
  
     Si el editor admite las búsquedas de texto imagen, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     En caso contrario, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Si implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> métodos, puede simplificar las tareas de la búsqueda mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaz.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>