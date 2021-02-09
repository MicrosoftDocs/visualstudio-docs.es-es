---
title: '&lt;&gt;elemento publisherIdentity (implementación ClickOnce) | Microsoft Docs'
description: El elemento publisherIdentity contiene información sobre el publicador que firmó un manifiesto de implementación. El elemento es necesario para los manifiestos firmados.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891298"
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

## <a name="remarks"></a>Notas

## <a name="requirements"></a>Requisitos

## <a name="subhead"></a>Subtítulo