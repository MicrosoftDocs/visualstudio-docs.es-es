---
title: "&lt;publisherIdentity&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 527ab7ae43790f7e824ead33fb601f0f8dee2bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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