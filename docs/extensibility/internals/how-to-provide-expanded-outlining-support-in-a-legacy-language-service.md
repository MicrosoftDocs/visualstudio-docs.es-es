---
title: "Proporciona compatibilidad en un servicio de lenguaje de esquematización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fd353e39e3e3edbdbdb929fa16abb74126dbbc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Cómo: proporcionar compatibilidad de esquematización expandida en un servicio de lenguaje heredado
Hay dos opciones para ampliar la compatibilidad de esquematización para el lenguaje más allá de admitir la **contraer a definiciones** comando. Puede agregar regiones de esquema controlados por el editor y agregar regiones de esquema controlado por el cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Agregar regiones de esquema controlados por Editor  
 Use este enfoque para crear una región de esquema y, a continuación, permitir que el editor controlar si la región está expandida, contraído y así sucesivamente. De las dos opciones para proporcionar compatibilidad con esquema, esta opción es el menos estable. Para esta opción, se crea una nueva área de esquema a través de un intervalo especificado de texto mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Después de crea esta región, su comportamiento se controla mediante el editor. Utilice el procedimiento siguiente para implementar regiones de esquema controlados por el editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar una región de controlados por el editor de esquema  
  
1.  Llame a `QueryService` para<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto dado. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para el búfer.  
  
3.  Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para agregar uno o más nuevos describir regiones a la vez.  
  
     Este método permite especificar el intervalo de texto al esquema, si las regiones de esquema existentes se quitan o se conservan, y si la región de esquema está expandido o contraído de manera predeterminada.  
  
## <a name="adding-client-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el cliente  
 Utilice este enfoque para la esquematización implemente controlado por el cliente (o inteligente) que se usa como el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] servicios de lenguaje. Un servicio de lenguaje que administra su propia esquematización supervisa el contenido del búfer de texto para destruirla antiguo regiones de esquema cuando deja de ser válido y para crear regiones de esquema nuevas según sea necesario.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar una región de esquema controlado por el cliente  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto dado. Esto determina si una sesión de texto oculto ya existe para el búfer.  
  
3.  Si existe ya una sesión de texto, no es necesario crear uno y un puntero a la existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto. Use este puntero para enumerar y crear regiones de esquema. De lo contrario, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para crear una sesión de texto oculto para el búfer. Un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto.  
  
    > [!NOTE]
    >  Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, puede especificar un cliente de texto oculto (es decir, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Este cliente le avisa cuando un texto oculto o región de esquema está expandido o contraído por el usuario.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> estructura) parámetro: especifique un valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que se está creando una región de esquema, en lugar de una región oculta. Especifique si la región está controlado por el cliente o controlados por el editor en el `dwBehavior` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de esquematización inteligente puede contener una combinación de regiones de esquema controlado por el cliente y el editor. Especifique el texto de titular que se muestra cuando la región de esquema está contraído, como "...", en la `pszBanner` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. Texto del titular del editor de la predeterminada para la región oculta es "...".