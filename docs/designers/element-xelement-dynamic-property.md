---
title: "Element (Propiedad dinámica de XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07be4c31e7bec729f9d6bdd77f522c5fe80b5bc6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="element-xelement-dynamic-property"></a>Element (Propiedad dinámica de XElement)
Obtiene un indizador que se utiliza para recuperar la instancia del elemento secundario que se corresponde con el nombre expandido especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un indizador del tipo `XElement Item(String expandedName)`. Este indizador toma un parámetro de nombre expandido y devuelve el <xref:System.Xml.Linq.XElement> correspondiente, o bien `null` si no existe ningún elemento con el nombre especificado.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Element%2A> de la clase <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)