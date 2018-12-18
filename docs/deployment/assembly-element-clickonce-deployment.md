---
title: '&lt;ensamblado&gt; elemento (implementación ClickOnce) | Microsoft Docs'
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
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9d72eafb03f22a01d22894bb887085648c324e3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080638"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;ensamblado&gt; elemento (implementación ClickOnce)
El elemento de nivel superior para el manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
 El `assembly` es el elemento raíz y es necesario. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos del manifiesto deben estar en los espacios de nombres siguientes: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, y `http://www.w3.org/2000/09/xmldsig#`. También deben ser elementos secundarios del ensamblado en estos espacios de nombres, mediante herencia o etiquetado.  
  
 El `assembly` elemento tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`manifestVersion`|Requerido. Este atributo debe establecerse en `1.0`.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `assembly` elemento en un manifiesto de implementación para una aplicación implementada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [del manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```xml  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<ensamblado > elemento](../deployment/assembly-element-clickonce-application.md)