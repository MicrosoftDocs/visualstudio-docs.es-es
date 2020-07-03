---
title: 'Cómo: usar elementos coloreables integrados | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905213"
---
# <a name="how-to-use-built-in-colorable-items"></a>Cómo: usar elementos coloreables integrados
Antes de usar los elementos coloreables integrados, primero debe indicar al entorno de desarrollo integrado (IDE) que no está proporcionando sus propios elementos coloreables personalizados, que en este caso serían <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objetos. Para ello, establezca una entrada del registro para el servicio de lenguaje.

## <a name="to-use-built-in-colorable-items"></a>Para usar elementos coloreables integrados

1. En **HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language Services \\<\> nombre de idioma**, donde \<X.Y> es una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y \<Language Name> es el nombre del idioma, cree un valor de entrada del registro DWORD denominado **RequestStockColors**.

2. Establezca el valor de la entrada del registro **RequestStockColors** en *1*.

    Después de crear la entrada del registro, el método de su coloreador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> puede utilizar los miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeración para rellenar la matriz de atributos de color que utiliza el editor.

   > [!NOTE]
   > No establezca esta entrada del registro si va a proporcionar elementos coloreables personalizados. Para obtener más información, vea [elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Vea también
- [Colores de la sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementar el color de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)
