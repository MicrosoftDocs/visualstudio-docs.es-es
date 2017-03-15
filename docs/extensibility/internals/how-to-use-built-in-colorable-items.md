---
title: "C&#243;mo: usar elementos coloreables integrados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elementos coloreables"
  - "Servicios de lenguaje, elementos coloreables integrados"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: usar elementos coloreables integrados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Antes de utilizar los elementos colorear integrados, deberá designar primero al IDE \(IDE\) que no es el proporcionar poseer los elementos colorear personalizados, que en este caso se objetos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> .  Esto se hace estableciendo una entrada de Registro del servicio de lenguaje.  
  
### Para usar elementos colorear integrados  
  
1.  En HKEY\_LOCAL\_MACHINE \\VisualStudio \\*X.Y*\\Languages\\Language Services \\*Nombre del lenguaje*, donde es una versión *X.Y* de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y *Nombre del lenguaje* es el nombre del lenguaje, cree un valor de entrada del Registro DWORD `RequestStockColors`denominado.  
  
2.  Establezca el valor de entrada del Registro de `RequestStockColors` en 1.  
  
     Después de crear la entrada del Registro, el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> de los colorizer pueden utilizar los miembros de la enumeración de <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> para completar la matriz de atributos de color para uso del editor.  
  
    > [!NOTE]
    >  No establezca esta entrada del Registro si está proporcionando elementos colorear personalizados.  Para obtener más información, vea [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md).  
  
## Vea también  
 [Colores en los editores personalizados de sintaxis](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colores en un servicio de lenguaje heredado de sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementación de colores de sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementos coloreables personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service2.md)