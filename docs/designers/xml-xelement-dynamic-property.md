---
title: Xml (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87796afcc06190a54a3670581be7700fa8d49061
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940565"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propiedad dinámica de XElement)

Obtiene el contenido XML sin formato del elemento.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un <xref:System.String> que representa el contenido XML sin formato del elemento.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Vea también

- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xelement-dynamic-property.md)