---
title: Proporcionar soporte técnico en un servicio de lenguaje de esquematización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a26d9dbc67f502e30968f3db89834b12e02ae3e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965556"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedimiento Proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado
Hay dos opciones para ampliar la compatibilidad con esquematización el lenguaje más allá de admitir la **contraer a definiciones** comando. Puede agregar regiones de esquema controlado por el editor y agregar regiones de esquema controlado por el cliente.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el editor  
 Utilice este enfoque para crear una región de esquema y, a continuación, permitir que el editor para controlar si la región está expandida, contraído y así sucesivamente. De las dos opciones para proporcionar compatibilidad con esquematización, esta opción es menos robusta. Para esta opción, cree una nueva región de esquema en un intervalo especificado de texto mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Una vez creada esta región, su comportamiento se controla mediante el editor. Utilice el procedimiento siguiente para implementar las regiones de esquema controlado por el editor.  
  
### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar una región de controlado por el editor de esquema  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero para un búfer de texto. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para el búfer.  
  
3.  Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para agregar uno o más nuevas regiones de esquema a la vez.  
  
     Este método permite especificar el intervalo de texto para el esquema, si se quitan o se conservan las regiones de esquema existente, y si la región de esquema se expande o contrae de forma predeterminada.  
  
## <a name="add-client-controlled-outline-regions"></a>Agregar regiones de esquema controlado por el cliente  
 Utilice este enfoque de esquematización implemente controlado por el cliente (o inteligente) que se usa como el [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] servicios de lenguaje. Un servicio de lenguaje que administra su propia esquematización supervisa el contenido del búfer de texto para destruir las regiones de esquema anterior cuando dejan de ser válidos y crear nuevas regiones de esquema, según sea necesario.  
  
### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar una región de esquema controlado por el cliente  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero para un búfer de texto. Esto determina si una sesión de texto oculto ya existe para el búfer.  
  
3.  Si una sesión de texto ya existe, no es necesario crear uno y un puntero a la existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto. Use este puntero para enumerar y crear regiones de esquema. En caso contrario, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para crear una sesión de texto oculto para el búfer. Un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto.  
  
    > [!NOTE]
    >  Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, puede especificar un cliente de texto oculto (es decir, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Este cliente le avisa cuando un texto oculto o región de esquema está expandido o contraído por el usuario.  
  
4.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> estructura) parámetro: Especifique un valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que va a crear una región de esquema, en lugar de una región oculta. Especifique si la región está controlado por el cliente o controlado por el editor en el `dwBehavior` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de esquematización inteligente puede contener una combinación de regiones de esquema controlado por el cliente y el editor. Especifique el texto del titular que se muestra cuando la región de esquema está contraído, por ejemplo, "...", en el `pszBanner` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. Texto de titular del editor predeterminado para una región oculta es "...".