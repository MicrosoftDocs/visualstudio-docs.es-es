---
title: '&lt;ensamblado&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd872053117388e9e08dcb8c4c2bfedcba622fd4
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077095"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;ensamblado&gt; elemento (aplicación ClickOnce)
El elemento de nivel superior para el manifiesto de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El `assembly` es el elemento raíz y es necesario. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos del manifiesto deben estar en uno de los espacios de nombres siguientes:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 También deben ser elementos secundarios del ensamblado en estos espacios de nombres, mediante herencia o etiquetado.  
  
 El `assembly` elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`manifestVersion`|Requerido. El `manifestVersion` atributo debe establecerse en `1.0`.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `assembly` elemento en un manifiesto de aplicación para un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```xml
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<ensamblado > elemento](../deployment/assembly-element-clickonce-deployment.md)
