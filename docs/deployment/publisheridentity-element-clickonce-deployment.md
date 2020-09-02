---
title: '&lt;&gt;elemento publisherIdentity (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927544"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento publisherIdentity (implementación ClickOnce)
Contiene información sobre el editor que firmó este manifiesto de implementación.

## <a name="syntax"></a>Sintaxis

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `publisherIdentity` elemento es necesario para los manifiestos firmados. En la tabla siguiente se muestran los atributos que `publisherIdentity` admite el elemento.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Necesario. Describe la identidad de la entidad que publicó esta aplicación.|
|`issuerKeyHash`|Necesario. Contiene el hash de SHA-1 de la clave pública del emisor del certificado.|

#### <a name="parameters"></a>Parámetros

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

## <a name="exceptions"></a>Excepciones

## <a name="remarks"></a>Observaciones

## <a name="requirements"></a>Requisitos

## <a name="subhead"></a>Subtítulo