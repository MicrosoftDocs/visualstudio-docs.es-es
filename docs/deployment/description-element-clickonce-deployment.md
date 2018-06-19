---
title: '&lt;descripción&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft'
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
ms.openlocfilehash: 06a8f1a1e5ec5f4663ed999566158d104c6a7364
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31564251"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;descripción&gt; elemento (implementación de ClickOnce)
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
 El elemento `description` es obligatorio y se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1`. No contiene elementos secundarios y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`publisher`|Requerido. Identifica el nombre de la empresa utilizado para la colocación del icono en las ventanas de **iniciar** menú y **agregar o quitar programas** elemento en el Panel de Control, cuando la implementación está configurada para la instalación.|  
|`product`|Requerido. Identifica el nombre completo del producto. Usar como el título del icono instalado en las ventanas de **iniciar** menú.|  
|`suiteName`|Opcional. Identifica una subcarpeta dentro de la `publisher` carpeta en las ventanas de **iniciar** menú.|  
|`supportUrl`|Opcional. Especifica una dirección URL de soporte técnico que se muestra en el **agregar o quitar programas** elemento en el Panel de Control. También se crea un acceso directo a esta dirección URL para la compatibilidad con la aplicación en las ventanas de **iniciar** menú, cuando la implementación está configurada para la instalación.|  
  
## <a name="remarks"></a>Comentarios  
 El elemento de descripción es necesario en todas las configuraciones de implementación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `description` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Este ejemplo de código forma parte de un ejemplo mayor proporcionado para el [manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)