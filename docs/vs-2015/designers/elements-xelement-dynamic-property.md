---
title: Elementos (Propiedad dinámica de XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664694"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtiene un indizador que se utiliza para recuperar los elementos secundarios del elemento actual que coinciden con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto
 Un indizador del tipo `IEnumerable<XElement> Item(String expandedName)`. Este indizador toma el nombre expandido de los elementos secundarios deseados y devuelve los elementos secundarios coincidentes en una recopilación <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Comentarios
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> de la clase <xref:System.Xml.Linq.XContainer>.

 Los elementos de la colección devuelta están en el orden del documento de origen XML.

 Esta propiedad usa la ejecución aplazada.

## <a name="see-also"></a>Vea también
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md) [Elemento](../designers/element-xelement-dynamic-property.md) [Descendientes](../designers/descendants-xelement-dynamic-property.md)
