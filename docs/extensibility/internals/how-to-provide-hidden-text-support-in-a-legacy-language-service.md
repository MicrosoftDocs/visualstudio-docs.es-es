---
title: "C&#243;mo: proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "oculta el texto, compatibilidad"
  - "editores [Visual Studio SDK], ocultados texto"
  - "Servicios de lenguaje, implementación de regiones de texto oculto"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede crear regiones de texto oculto además de regiones de esquema.  Las regiones de texto oculto se pueden cliente\-controlar o editor\-controlar y se utilizan para ocultar un área de texto completo.  El editor muestra una región oculta como líneas horizontales.  Un ejemplo de esto es la vista sólo script en el editor HTML.  
  
## Procedimiento  
  
#### Para implementar un área de texto oculto  
  
1.  llamada `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto.  Determina si una sesión de texto oculto ya existe en el búfer.  
  
3.  Si no existe aún, no necesita crear uno y un puntero al objeto existente de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve.  Utilice este puntero para enumerar y crear regiones de texto oculto.  Si no, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> de llamada para crear una sesión de texto oculto para el búfer.  
  
     Un puntero al objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve.  
  
    > [!NOTE]
    >  Cuando se llama a `CreateHiddenTextSession`, puede especificar un cliente de texto oculto \(es decir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\).  El cliente de texto oculto notifica cuándo el texto oculto o esquematización está contraído o expandido por el usuario.  
  
4.  Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> para agregar una o más recientes regiones de esquema al mismo tiempo, especificando la siguiente información en el parámetro de `reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\):  
  
    1.  Especifique un valor de `hrtConcealed` en el miembro de `iType` de la estructura de <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> para indicar que se está creando una región oculta, en lugar de una región de esquema.  
  
        > [!NOTE]
        >  Cuando se encubiertas se oculta a las áreas, líneas de muestra el editor automáticamente alrededor de las regiones ocultas que indican su presencia.  
  
    2.  especifique si la región cliente\-está controlada o editor\-controlada en los miembros de `dwBehavior` de la estructura de <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> .  La implementación automática de esquematización puede contener una combinación de regiones cliente\-controladas del publicador y del esquema y el texto oculto.