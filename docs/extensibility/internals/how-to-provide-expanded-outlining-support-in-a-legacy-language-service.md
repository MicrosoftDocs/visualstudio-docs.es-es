---
title: "Proporcionar soporte técnico en un servicio de lenguaje de esquematización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Cómo: proporcionar soporte ampliado de esquematización en un servicio de lenguaje heredado
Hay dos opciones para ampliar la compatibilidad de esquematización para el lenguaje más allá de admitir el **contraer a definiciones** comando. Puede agregar regiones de esquema de control de editor y agregar regiones de esquema controlado por el cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Agregar regiones de esquema de control de Editor  
 Utilice este enfoque para crear una región de esquema y, a continuación, permitir que el editor controlar si se expande la región, se contrae y así sucesivamente. De las dos opciones para proporcionar compatibilidad con esquema, esta opción es menos sólida. Para esta opción, se crea una nueva área de esquema en un intervalo especificado de texto mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Después de crea esta región, su comportamiento se controla mediante el editor. Utilizar el siguiente procedimiento para implementar regiones de esquema controlado por el editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar una región controlado por el editor de esquema  
  
1.  Llame a `QueryService` para<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto dado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>objeto para el búfer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Llamar a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>para agregar uno o más nuevas regiones de esquema a la vez.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Este método le permite especificar el intervalo de texto al esquema, si las regiones de esquema existentes se quitan o se conservan, y si la región de esquema está expandida o contraída de manera predeterminada.  
  
## <a name="adding-client-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el cliente  
 Utilice este enfoque de esquematización implemente controlado por el cliente (ni inteligente) que se usa como el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] servicios de lenguaje. Un servicio de lenguaje que administra su propio esquema supervisa el contenido del búfer de texto para destruir antiguo regiones de esquema cuando deja de ser válido y crear nuevas regiones de esquema según sea necesario.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar una región de esquema controlado por el cliente  
  
1.  Llame a `QueryService` de <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto dado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Determina si existe ya una sesión de texto oculto para el búfer.  
  
3.  Si el texto ya existe una sesión, entonces no es necesario crear uno y un puntero a la existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>devuelve el objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Utilice este puntero para enumerar y crear regiones de esquema. De lo contrario, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>para crear una sesión de texto oculto para el búfer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>devuelve el objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, puede especificar un cliente de texto oculto (es decir, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>objeto).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Este cliente le notifica cuando un texto oculto o región de esquema está expandido o contraído por el usuario.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>estructura) parámetro: especifique un valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>en la `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estructura para indicar que va a crear una región de esquema, en lugar de la región oculta.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Especifique si la región está controlado por el cliente o controlados por el editor en el `dwBehavior` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estructura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> La implementación de esquematización inteligente puede contener una mezcla de regiones de esquema controlado por el cliente y el editor. Especificar el texto del titular que se muestra cuando la región de esquema está contraída, como "...", en la `pszBanner` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>estructura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Texto de titular del editor predeterminado para la región oculta es "...".
