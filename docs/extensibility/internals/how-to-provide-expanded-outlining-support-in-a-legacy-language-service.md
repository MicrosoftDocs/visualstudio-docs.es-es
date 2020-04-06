---
title: Proporcionar soporte de esquematización en un servicio de idiomas Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707970"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Cómo: Proporcionar soporte de esquematización ampliada en un servicio de lenguaje heredado
Hay dos opciones para ampliar la compatibilidad de esquematización para su idioma más allá de admitir el **comando Contraer a definiciones.** Puede agregar regiones de esquema controladas por el editor y regiones de esquema controladas por el cliente.

## <a name="adding-editor-controlled-outline-regions"></a>Adición de regiones de esquema controladas por el editor
 Use este enfoque para crear una región de esquema y, a continuación, permita que el editor controle si la región está expandida, contraída, etc. De las dos opciones para proporcionar soporte de esquematización, esta opción es la menos robusta. Para esta opción, se crea una nueva región de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>esquema en un intervalo de texto especificado mediante . Después de crear esta región, el editor controla su comportamiento. Use el siguiente procedimiento para implementar regiones de esquema controladas por el editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Implementar una región de esquema controlada por el editor

1. Llamar `QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Esto devuelve un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntero a .

2. Llamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a , pasando un puntero para un búfer de texto determinado. Esto devuelve un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> puntero al objeto para el búfer.

3. Llame <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> para un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>puntero a .

4. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para agregar una o más regiones de esquema nuevas a la vez.

     Este método permite especificar el intervalo de texto que se va a esbozar, si se quitan o conservan las regiones de esquema existentes y si la región de esquema se expande o contrae de forma predeterminada.

## <a name="add-client-controlled-outline-regions"></a>Agregar regiones de esquema controladas por el cliente
 Utilice este enfoque para implementar la esquematización controlada por [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] el [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] cliente (o inteligente) como la utilizada por los servicios de lenguaje y. Un servicio de lenguaje que administra su propia esquematización supervisa el contenido del búfer de texto con el fin de destruir las regiones de esquema antiguas cuando dejan de ser válidas y para crear nuevas regiones de esquema según sea necesario.

### <a name="to-implement-a-client-controlled-outline-region"></a>Implementar una región de esquema controlada por el cliente

1. Llame `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>para . Esto devuelve un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntero a .

2. Llamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a , pasando un puntero para un búfer de texto determinado. Esto determina si ya existe una sesión de texto oculto para el búfer.

3. Si ya existe una sesión de texto, no es necesario <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> crear una y se devuelve un puntero al objeto existente. Utilice este puntero para enumerar y crear regiones de esquema. De lo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> contrario, llame para crear una sesión de texto oculto para el búfer. Se devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un puntero al objeto.

    > [!NOTE]
    > Cuando se <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>llama a , puede especificar un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> cliente de texto oculto (es decir, un objeto). Este cliente le notifica cuando el usuario expande o contrae un texto oculto o una región de esquema.

4. Parámetro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> de estructura de llamada): `iType` especifique un <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> valor de <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> en el miembro de la estructura para indicar que está creando una región de esquema, en lugar de una región oculta. Especifique si la región está controlada por el `dwBehavior` cliente o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> por el editor en el miembro de la estructura. La implementación de esquematización inteligente puede contener una combinación de regiones de esquema controladas por el editor y el cliente. Especifique el texto del banner que se muestra cuando se contrae `pszBanner` la región <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> de esquema, como "...", en el miembro de la estructura. El texto de banner predeterminado del editor para una región oculta es "...".
