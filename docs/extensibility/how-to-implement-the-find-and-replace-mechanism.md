---
title: Procedimiento Implementar la buscar y reemplazar el mecanismo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3847b9125109cd48b458d06cbfc41fa91b7139f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943030"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Procedimiento Implementar la buscar y reemplazar el mecanismo de

Visual Studio proporciona dos maneras de implementar la búsqueda y reemplazo. Una consiste en pasar de una imagen de texto en el shell y permitirle controlar la búsqueda, el resaltado y reemplazar texto. Esto permite a los usuarios especificar varios intervalos de texto. Como alternativa, el VSPackage puede controlar esta funcionalidad propia. En ambos casos debe notificar al shell sobre el destino actual y los destinos para todos los documentos abiertos.

## <a name="to-implement-findreplace"></a>Para implementar la búsqueda y reemplazo

1. Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaz en uno de los objetos devueltos por las propiedades de marco <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Si va a crear un editor personalizado, debe implementar esta interfaz como parte de la clase de editor personalizado.

2. Use el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar las opciones que admite el editor y para indicar si implementa la búsqueda de imágenes de texto.

   Si el editor admite la búsqueda de imágenes de texto, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   En caso contrario, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. Si implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> métodos, puede simplificar las tareas de búsqueda mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaz.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>