---
title: Element (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 520df74dae14fe672eb7d3db1bdc23a0a6437b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976763"
---
# <a name="element-xelement-dynamic-property"></a>Element (Propiedad dinámica de XElement)

Obtiene un indizador que se utiliza para recuperar la instancia del elemento secundario que se corresponde con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un indizador del tipo `XElement Item(String expandedName)`. Este indizador toma un parámetro de nombre expandido y devuelve el <xref:System.Xml.Linq.XElement> correspondiente, o bien `null` si no existe ningún elemento con el nombre especificado.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Element%2A> de la clase <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)