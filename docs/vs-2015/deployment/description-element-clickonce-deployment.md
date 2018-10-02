---
title: '&lt;descripción&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 473ebf814ab65c34ee99cab0cf2cc239e0d013eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565876"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;descripción&gt; elemento (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;descripción&gt; elemento (implementación ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/description-element-clickonce-deployment).  
  
Identifica la información de la aplicación utilizada para crear una presencia de shell y un **agregar o quitar programas** elemento en el Panel de Control.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
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
 En el ejemplo de código siguiente se ilustra un `description` elemento en un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [del manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)



