---
title: 'Cómo: proporcionar compatibilidad en texto oculto en un servicio de lenguaje heredado | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54e508c6bcbb9cb79459e0b61a97f51350c00708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Cómo: proporcionar compatibilidad en texto oculto en un servicio de lenguaje heredado
Puede crear áreas de texto oculto además de regiones de esquema. Regiones de texto oculto pueden estar controlado por el cliente o controlados por el editor y se utilizan para ocultar una porción de texto completo. El editor muestra una región oculta como líneas horizontales. Un ejemplo de esto es la vista sólo secuencias de comandos en el editor HTML.  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-implement-a-hidden-text-region"></a>Para implementar un área de texto oculto  
  
1.  Llame a `QueryService` para <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Esto devuelve un puntero a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, pasando un puntero a un búfer de texto dado. Esto determina si una sesión de texto oculto ya existe para el búfer.  
  
3.  Si ya existe uno, no es necesario crear uno y un puntero a la existente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto. Use este puntero para enumerar y crear áreas de texto oculto. De lo contrario, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> para crear una sesión de texto oculto para el búfer.  
  
     Un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se devuelve el objeto.  
  
    > [!NOTE]
    >  Cuando se llama a `CreateHiddenTextSession`, puede especificar un cliente de texto oculto (es decir, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). El cliente de texto oculto le avisa cuando el texto oculto o esquematización está expandida o contraída por el usuario.  
  
4.  Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> para agregar uno o más nuevos describir regiones a la vez, especifique la siguiente información en el `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parámetro:  
  
    1.  Especifique un valor de `hrtConcealed` en el `iType` miembro de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura para indicar que se está creando una región oculta, en lugar de una región de esquema.  
  
        > [!NOTE]
        >  Cuando se ocultan las regiones ocultos, el editor muestra automáticamente líneas en torno a las regiones ocultas para indicar su presencia.  
  
    2.  Especifique si la región está controlado por el cliente o controlados por el editor en el `dwBehavior` los miembros de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> estructura. La implementación de esquematización inteligente puede contener una combinación de regiones de texto oculto y controlado por el cliente y el editor de esquema.