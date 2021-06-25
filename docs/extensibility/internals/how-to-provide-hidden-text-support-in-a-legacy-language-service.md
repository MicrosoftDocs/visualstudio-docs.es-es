---
title: Proporcionar compatibilidad con texto oculto en el servicio de lenguaje heredado
description: Aprenda a proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado mediante la adición de regiones de texto oculto controladas por el editor o controladas por el cliente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31c62f50cfff8662c543d24dceabdb429a9b9b05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901791"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Cómo: Proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado
Puede crear regiones de texto ocultas además de las regiones de esquema. Las regiones de texto ocultas pueden controlarse por el cliente o controlarse por el editor y se usan para ocultar completamente una región de texto. El editor muestra una región oculta como líneas horizontales. Un ejemplo de esto es la **vista Solo** script en el editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Para implementar una región de texto oculta

1. Llame `QueryService` a para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> a , pasando un puntero para un búfer de texto determinado. Esto determina si ya existe una sesión de texto oculto para el búfer.

3. Si ya existe uno, no es necesario crear uno y se devuelve un puntero al objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> existente. Use este puntero para enumerar y crear regiones de texto ocultas. De lo contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> llame a para crear una sesión de texto oculto para el búfer.

     Se devuelve un puntero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> al objeto .

    > [!NOTE]
    > Al llamar a `CreateHiddenTextSession` , puede especificar un cliente de texto oculto (es decir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). El cliente de texto oculto le notifica cuando el usuario expande o contrae el texto oculto o la línea.

4. Llame a para agregar una o varias regiones de esquema nuevas a la vez, especificando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> siguiente información en el parámetro ( `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ):

    1. Especifique un valor de en el miembro de la estructura para indicar que está creando una región oculta, en lugar de `hrtConcealed` `iType` una región de <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> esquema.

        > [!NOTE]
        > Cuando las regiones ocultas están ocultas, el editor muestra automáticamente líneas alrededor de las regiones ocultas para indicar su presencia.

    2. Especifique si la región está controlada por el cliente o controlada por el editor en `dwBehavior` los miembros de la estructura <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . La implementación de esquematización inteligente puede contener una combinación de regiones de texto oculto y esquema controlado por el editor y el cliente.
