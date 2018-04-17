---
title: 'Cómo: implementar la buscar y reemplazar mecanismo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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