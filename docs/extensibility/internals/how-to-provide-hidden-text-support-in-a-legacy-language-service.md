---
title: Proporcionar compatibilidad con texto oculto en el servicio de lenguaje heredado
description: Obtenga información sobre cómo proporcionar compatibilidad de texto oculto en un servicio de lenguaje heredado mediante la adición de regiones de texto oculto controladas por el editor o por el cliente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f51f8e0c5ca268c1171804f663e5d01bd7c2530
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761314"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Cómo: proporcionar compatibilidad de texto oculto en un servicio de lenguaje heredado
Puede crear regiones de texto oculto además de regiones de esquema. Las regiones de texto oculto pueden ser controladas por el cliente o por el editor, y se usan para ocultar una región de texto por completo. El editor muestra una región oculta como líneas horizontales. Un ejemplo de esto es la vista **solo script** en el editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Para implementar una región de texto oculto

1. Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , pasando un puntero para un búfer de texto determinado. Determina si ya existe una sesión de texto oculto para el búfer.

3. Si ya existe una, no es necesario crear una y se devuelve un puntero al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto existente. Utilice este puntero para enumerar y crear regiones de texto ocultas. De lo contrario, llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> a para crear una sesión de texto oculto para el búfer.

     Se devuelve un puntero al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> objeto.

    > [!NOTE]
    > Al llamar a `CreateHiddenTextSession` , puede especificar un cliente de texto oculto (es decir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). El cliente de texto oculto le notifica cuando el usuario o el texto oculto se expande o contrae.

4. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> a para agregar una o varias regiones de esquema nuevas a la vez, especificando la siguiente información en el `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> parámetro ():

    1. Especifique un valor de `hrtConcealed` en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que está creando una región oculta, en lugar de una región de esquema.

        > [!NOTE]
        > Cuando se ocultan las regiones ocultas, el editor muestra automáticamente las líneas alrededor de las regiones ocultas para indicar su presencia.

    2. Especifique si la región está controlada por el cliente o por el editor en los `dwBehavior` miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de la esquematización inteligente puede contener una combinación de regiones de texto oculto y de esquema controlado por el cliente y el editor.
