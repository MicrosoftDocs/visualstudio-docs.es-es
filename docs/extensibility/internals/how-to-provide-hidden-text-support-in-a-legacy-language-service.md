---
title: Proporcionar compatibilidad con texto oculto en el servicio de lenguaje heredado
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
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707925"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Cómo: Proporcionar soporte de texto oculto en un servicio de lenguaje heredado
Puede crear regiones de texto ocultas además de regiones de esquema. Las regiones de texto ocultas pueden estar controladas por el cliente o por el editor y se utilizan para ocultar una región de texto por completo. El editor muestra una región oculta como líneas horizontales. Un ejemplo de esto es la vista **Solo script** en el editor HTML.

## <a name="to-implement-a-hidden-text-region"></a>Para implementar una región de texto oculto

1. Llame `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>para .

     Esto devuelve un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntero a .

2. Llamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>a , pasando un puntero para un búfer de texto determinado. Esto determina si ya existe una sesión de texto oculto para el búfer.

3. Si ya existe uno, no es necesario crear uno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> y se devuelve un puntero al objeto existente. Utilice este puntero para enumerar y crear regiones de texto ocultas. De lo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> contrario, llame para crear una sesión de texto oculto para el búfer.

     Se devuelve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un puntero al objeto.

    > [!NOTE]
    > Al llamar `CreateHiddenTextSession`a , puede especificar un cliente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>de texto oculto (es decir, ). El cliente de texto oculto le notifica cuando el usuario expande o contrae texto oculto o esquematización.

4. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> para agregar una o más regiones de esquema nuevas a la vez, especificando la siguiente información en el `reHidReg` parámetro (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>):

    1. Especifique un `hrtConcealed` valor `iType` de en <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> el miembro de la estructura para indicar que está creando una región oculta, en lugar de una región de esquema.

        > [!NOTE]
        > Cuando las regiones ocultas están ocultas, el editor muestra automáticamente las líneas alrededor de las regiones ocultas para indicar su presencia.

    2. Especifique si la región está controlada por el `dwBehavior` cliente o <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> por el editor en los miembros de la estructura. La implementación de esquematización inteligente puede contener una combinación de esquemas controlados por el editor y el cliente y regiones de texto ocultas.
