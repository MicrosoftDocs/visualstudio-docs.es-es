---
title: Xml (Propiedad dinámica de XElement) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6daf831030fd02f3aa1e3a4844a42ba60bf0574c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175817"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtiene el contenido XML sin formato del elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un <xref:System.String> que representa el contenido XML sin formato del elemento.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xelement-dynamic-property.md)



