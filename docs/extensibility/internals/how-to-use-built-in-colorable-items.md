---
title: 'Cómo: usar elementos coloreables integrados | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 658b024a57912bf96a7988363f2bf363e9cb1f0a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512621"
---
# <a name="how-to-use-built-in-colorable-items"></a>Cómo: usar elementos coloreables integrados
Antes de usar los elementos coloreables integrados, debe en primer lugar señalar al entorno de desarrollo integrado (IDE) que no proporcionan sus propios elementos coloreables personalizados, que en este caso sería <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objetos. Para ello, establezca una entrada del registro del servicio de lenguaje.  
  
## <a name="to-use-built-in-colorable-items"></a>Para usar elementos coloreables integrados  
  
1.  En **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language Services\\< Nombreidioma\>**, donde \<X.Y > es una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y \<Nombreidioma > es el nombre de su lenguaje, cree un valor de entrada del Registro DWORD llamado **RequestStockColors**.  
  
2.  Establecer el **RequestStockColors** valores de entrada del registro para *1*.  
  
     Después de crear la entrada del registro, el Coloreador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método puede utilizar los miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeración para rellenar la matriz de atributos de color para su uso por el editor.  
  
    > [!NOTE]
    >  No establezca esta entrada del registro si va a proporcionar elementos coloreables personalizados. Para obtener más información, consulte [elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Vea también  
 [Colores de sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementación de colores de sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)