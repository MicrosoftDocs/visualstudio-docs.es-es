---
title: '&lt;descripción&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8985bc83299f55cec3c5f41fd3d76c8801fdf34
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079815"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;descripción&gt; elemento (implementación ClickOnce)
Identifica la información de la aplicación utilizada para crear una presencia de shell y un **agregar o quitar programas** elemento en el Panel de Control.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El elemento `description` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1`. No contiene elementos secundarios y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`publisher`|Requerido. Identifica el nombre de la empresa utilizado para la ubicación del icono en el Windows **iniciar** menú y el **agregar o quitar programas** elemento en el Panel de Control, cuando la implementación está configurada para la instalación.|  
|`product`|Requerido. Identifica el nombre completo del producto. Usa como título para el icono instalado en el Windows **iniciar** menú.|  
|`suiteName`|Opcional. Identifica una subcarpeta dentro de la `publisher` carpeta en el Windows **iniciar** menú.|  
|`supportUrl`|Opcional. Especifica una dirección URL de soporte técnico que se muestra en el **agregar o quitar programas** elemento en el Panel de Control. También se crea un acceso directo a esta dirección URL para la compatibilidad de la aplicación en el Windows **iniciar** menú cuando la implementación está configurada para la instalación.|  
  
## <a name="remarks"></a>Comentarios  
 Se requiere el elemento description en todas las configuraciones de implementación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `description` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [del manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```xml  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)