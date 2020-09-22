---
title: 'Cómo: usar elementos coloreables integrados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842478"
---
# <a name="how-to-use-built-in-colorable-items"></a>Uso de elementos coloreables integrados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Antes de usar los elementos coloreables integrados, primero debe indicar al entorno de desarrollo integrado (IDE) que no está proporcionando sus propios elementos coloreables personalizados, que en este caso serían <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objetos. Para ello, establezca una entrada del registro para el servicio de lenguaje.  
  
### <a name="to-use-built-in-colorable-items"></a>Para usar elementos coloreables integrados  
  
1. En HKEY_LOCAL_MACHINE \VisualStudio \\ *x. y*\Languages\Language Services \\ *nombre de idioma*, donde *X. y* es una versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y el nombre del *idioma* es el nombre del idioma, cree un valor de entrada del registro DWORD denominado `RequestStockColors` .  
  
2. Establezca el `RequestStockColors` valor de entrada del registro en 1.  
  
     Después de crear la entrada del registro, el método de su coloreador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> puede utilizar los miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeración para rellenar la matriz de atributos de color que utiliza el editor.  
  
    > [!NOTE]
    > No establezca esta entrada del registro si va a proporcionar elementos coloreables personalizados. Para obtener más información, vea [elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Consulte también  
 [Colores de la sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementar el color de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)
