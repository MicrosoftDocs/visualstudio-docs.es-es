---
title: "Attribute (Propiedad dinámica de XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fd01945c2a33f3929f59e66a02a1d08a39c3cc7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (Propiedad dinámica de XElement)
Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un indizador del tipo `XAttribute Item(String expandedName)`. Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xattribute-dynamic-property.md)