---
title: "Cómo: usar elementos coloreables integrados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 545d5fa19182678ec1610fa7b689332e272f9962
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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