---
title: '&lt;&gt;elemento publisherIdentity (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 486e0bc5059e041f02e8dac4836c5ff59b27f63e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157633"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento publisherIdentity (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene información sobre el editor que firmó este manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
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
