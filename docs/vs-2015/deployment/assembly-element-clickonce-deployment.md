---
title: '&lt;ensamblado&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5fa45d64956fe1347477abb533e45565f27996f7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259953"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;ensamblado&gt; elemento (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento de nivel superior para el manifiesto de implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `assembly` es el elemento raíz y es necesario. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos del manifiesto deben estar en los espacios de nombres siguientes: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, y `http://www.w3.org/2000/09/xmldsig#`. También deben ser elementos secundarios del ensamblado en estos espacios de nombres, mediante herencia o etiquetado.  
  
 El elemento `assembly` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`manifestVersion`|Requerido. Este atributo debe establecerse en `1.0`.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `assembly` elemento en un manifiesto de implementación para una aplicación implementada mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [del manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) tema.  
  
```  
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



