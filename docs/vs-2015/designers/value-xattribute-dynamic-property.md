---
title: Value (Propiedad dinámica de XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187511"
---
# <a name="value-xattribute-dynamic-property"></a>Value (Propiedad dinámica de XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
