---
title: "Elementos (Propiedad dinámica de XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b28407d0b69d1ac7e2309ee1f8c24393b68e84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="elements-xelement-dynamic-property"></a>Elements (Propiedad dinámica de XElement)
Obtiene un indizador que se utiliza para recuperar los elementos secundarios del elemento actual que coinciden con el nombre expandido especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un indizador del tipo `IEnumerable<XElement> Item(String expandedName)`. Este indizador toma el nombre expandido de los elementos secundarios deseados y devuelve los elementos secundarios coincidentes en una recopilación <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> de la clase <xref:System.Xml.Linq.XContainer>.  
  
 Los elementos de la colección devuelta están en el orden del documento de origen XML.  
  
 Esta propiedad usa la ejecución aplazada.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Element](../designers/element-xelement-dynamic-property.md)   
 [Descendants](../designers/descendants-xelement-dynamic-property.md)