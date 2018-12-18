---
title: 'Cómo: proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56d125cdfc3cbdbbc880e1e8a98136eb20e07df1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774216"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Cómo: proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hay dos opciones para ampliar la compatibilidad con esquematización el lenguaje más allá de admitir la **contraer a definiciones** comando. Puede agregar regiones de esquema controlado por el editor y agregar regiones de esquema controlado por el cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el Editor  
 Utilice este enfoque para crear una región de esquema y, a continuación, permitir que el editor para controlar si la región está expandida, contraído y así sucesivamente. De las dos opciones para proporcionar compatibilidad con esquematización, esta opción es menos robusta. Para esta opción, cree una nueva región de esquema en un intervalo especificado de texto mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Una vez creada esta región, su comportamiento se controla mediante el editor. Utilice el procedimiento siguiente para implementar las regiones de esquema controlado por el editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar una región de controlado por el editor de esquema  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero para un búfer de texto. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para el búfer.  
  
3.  Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para agregar uno o más nuevas regiones de esquema a la vez.  
  
     Este método permite especificar el intervalo de texto para el esquema, si se quitan o se conservan las regiones de esquema existente, y si la región de esquema se expande o contrae de forma predeterminada.  
  
## <a name="adding-client-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el cliente  
 Utilice este enfoque de esquematización implemente controlado por el cliente (o inteligente) que se usa como el [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] servicios de lenguaje. Un servicio de lenguaje que administra su propia esquematización supervisa el contenido del búfer de texto para destruir las regiones de esquema anterior cuando deja de ser válido y crear nuevas regiones de esquema, según sea necesario.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar una región de esquema controlado por el cliente  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero para un búfer de texto. Esto determina si una sesión de texto oculto ya existe para el búfer.  
  
3.  Si una sesión de texto ya existe, no es necesario crear uno y un puntero a la existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto. Use este puntero para enumerar y crear regiones de esquema. En caso contrario, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para crear una sesión de texto oculto para el búfer. Un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto.  
  
    > [!NOTE]
    >  Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, puede especificar un cliente de texto oculto (es decir, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Este cliente le avisa cuando un texto oculto o región de esquema está expandido o contraído por el usuario.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> estructura) parámetro: especifique un valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que va a crear una región de esquema, en lugar de una región oculta. Especifique si la región está controlado por el cliente o controlado por el editor en el `dwBehavior` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de esquematización inteligente puede contener una combinación de regiones de esquema controlado por el cliente y el editor. Especifique el texto del titular que se muestra cuando la región de esquema está contraído, por ejemplo, "...", en el `pszBanner` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. Texto de titular del editor predeterminado para una región oculta es "...".

