---
title: 'Cómo: usar elementos coloreables integrados | Documentos de Microsoft'
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
ms.openlocfilehash: a6cf51516677aeca71dba269bcdd132e0830b6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129688"
---
# <a name="how-to-use-built-in-colorable-items"></a>Cómo: usar elementos coloreables integrados
Antes de usar los elementos coloreables integrados, debe en primer lugar indican al entorno de desarrollo integrado (IDE) que no proporcionan sus propios elementos coloreables personalizados, que en este caso sería <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objetos. Para ello, establezca una entrada del registro para el servicio de lenguaje.  
  
### <a name="to-use-built-in-colorable-items"></a>Utilizar elementos coloreables integrados  
  
1.  En HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language servicios\\*Nombreidioma*, donde *X.Y* es una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y *Nombreidioma* es el nombre de su idioma, cree un valor de entrada de Registro DWORD llamado `RequestStockColors`.  
  
2.  Establecer el `RequestStockColors` valor de la entrada del registro en 1.  
  
     Después de crear la entrada del registro, el aplicador de color <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método puede utilizar los miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumeración para rellenar la matriz de atributos de color para su uso por el editor.  
  
    > [!NOTE]
    >  No establezca esta entrada del registro si va a proporcionar elementos coloreables personalizados. Para obtener más información, consulte [elementos coloreable personalizado](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de color en los editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Color de un servicio de lenguaje heredado sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Color de la sintaxis de implementación](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)