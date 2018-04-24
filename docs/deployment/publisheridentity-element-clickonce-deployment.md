---
title: '&lt;publisherIdentity&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ad10cae4ebd3aee6b65ad408ea3a3df3f82fd02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (implementación de ClickOnce)
Contiene información sobre el editor que firmó este manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `publisherIdentity` elemento es necesario para los manifiestos firmados. La siguiente tabla muestra los atributos que la `publisherIdentity` admite el elemento.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`name`|Requerido. Describe la identidad de la entidad que publicó esta aplicación.|  
|`issuerKeyHash`|Requerido. Contiene el hash SHA-1 de la clave pública del emisor del certificado.|  
  
#### <a name="parameters"></a>Parámetros  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
  
## <a name="exceptions"></a>Excepciones  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="subhead"></a>Subtítulo