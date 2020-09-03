---
title: Proporcionar compatibilidad con la esquematización en un servicio de lenguaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 450ef1430e86467d116cc635a27600756bc36075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905288"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Cómo: proporcionar compatibilidad de esquematización ampliada en un servicio de lenguaje heredado
Hay dos opciones para ampliar la compatibilidad con la esquematización del lenguaje más allá del comando **contraer a definiciones** . Puede Agregar regiones de esquema controladas por el editor y agregar regiones de esquema controladas por el cliente.

## <a name="adding-editor-controlled-outline-regions"></a>Agregar regiones de esquema controladas por el editor
 Utilice este enfoque para crear una región de esquema y, a continuación, permitir que el editor Controle si la región se expande, se contrae, etc. De las dos opciones para proporcionar compatibilidad con la esquematización, esta opción es la menos robusta. En esta opción, se crea una nueva región de esquema en un intervalo de texto especificado mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Después de crear esta región, el editor controla su comportamiento. Utilice el procedimiento siguiente para implementar regiones de esquema controladas por el editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Para implementar una región de esquema controlada por el editor

1. Llamar a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , pasando un puntero para un búfer de texto determinado. Esto devuelve un puntero al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto para el búfer.

3. Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> a para agregar una o varias regiones de esquema nuevas a la vez.

     Este método permite especificar el intervalo de texto que se va a esquematizar, si se quitan o se conservan las regiones de esquema existentes, y si la región de esquema se expande o se contrae de forma predeterminada.

## <a name="add-client-controlled-outline-regions"></a>Agregar regiones de esquema controladas por el cliente
 Utilice este enfoque para implementar la esquematización controlada por el cliente (o inteligente) como la utilizada por los [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] servicios de lenguaje de y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . Un servicio de lenguaje que administra su propia esquematización supervisa el contenido del búfer de texto para destruir las regiones de esquema antiguas cuando dejan de ser válidas y para crear nuevas regiones de esquema según sea necesario.

### <a name="to-implement-a-client-controlled-outline-region"></a>Para implementar una región de esquema controlada por el cliente

1. Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , pasando un puntero para un búfer de texto determinado. Determina si ya existe una sesión de texto oculto para el búfer.

3. Si ya existe una sesión de texto, no es necesario crear una y se devuelve un puntero al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto existente. Utilice este puntero para enumerar y crear regiones de esquema. De lo contrario, llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> a para crear una sesión de texto oculto para el búfer. Se devuelve un puntero al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto.

    > [!NOTE]
    > Al llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , puede especificar un cliente de texto oculto (es decir, un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> objeto). Este cliente le envía una notificación cuando el usuario expande o contrae una región de texto o de esquema oculta.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Parámetro de la estructura de llamada): especifique un valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que está creando una región de esquema, en lugar de una región oculta. Especifique si la región está controlada por el cliente o por el editor en el `dwBehavior` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de la esquematización inteligente puede contener una combinación de regiones de esquema controlado por el cliente y el editor. Especifique el texto del titular que se muestra cuando se contrae la región del esquema, como "...", en el `pszBanner` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. El texto de banner predeterminado del editor para una región oculta es "...".
