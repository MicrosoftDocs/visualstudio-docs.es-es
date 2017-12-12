---
title: "Value (Propiedad dinámica de XAttribute) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d647e7623820c6621f6605277a695a98454fec5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="value-xattribute-dynamic-property"></a>Value (Propiedad dinámica de XAttribute)
Obtiene o establece el valor del atributo XML.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 <xref:System.String> que contiene el valor de este atributo.  
  
## <a name="exceptions"></a>Excepciones  
  
|Tipo de excepción|Condición|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Cuando se establece, el parámetro `value` es `null`.|  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente a la propiedad <xref:System.Xml.Linq.XAttribute.Value%2A> de la clase <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, pero su propiedad dinámica también admite las notificaciones de cambio.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attribute](../designers/attribute-xelement-dynamic-property.md)