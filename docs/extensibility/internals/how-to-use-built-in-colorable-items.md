---
title: 'Cómo: Usar elementos coloreables incorporados ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707785"
---
# <a name="how-to-use-built-in-colorable-items"></a>Cómo: Usar elementos coloreables incorporados
Antes de utilizar los elementos coloreables integrados, primero debe indicar al entorno de desarrollo integrado (IDE) que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> no está proporcionando sus propios elementos coloreables personalizados, que en este caso serían objetos. Para ello, establezca una entrada del Registro para el servicio de lenguaje.

## <a name="to-use-built-in-colorable-items"></a>Para usar elementos coloreables integrados

1. En **HKEY_LOCAL_MACHINE,VisualStudio\\<X.Y>,\\ Languages,\>Language Services<Language Name** \<, donde \<X.Y> es una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y Language Name> es el nombre de su idioma, cree un valor de entrada de registro DWORD denominado **RequestStockColors**.

2. Establezca el valor de entrada del Registro **RequestStockColors** en *1*.

    Después de crear la entrada del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Registro, el método <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> del colorante puede usar los miembros de la enumeración para rellenar la matriz de atributos de color para su uso por el editor.

   > [!NOTE]
   > No establezca esta entrada del Registro si proporciona elementos coloreables personalizados. Para obtener más información, consulte [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Vea también
- [Coloración de sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloreación de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementación de coloración de sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)
- [Artículos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)
- [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)
