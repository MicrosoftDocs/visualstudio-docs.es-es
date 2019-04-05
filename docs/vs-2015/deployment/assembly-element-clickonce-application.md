---
title: '&lt;ensamblado&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d619b8b3cd81e5b00fc689077a95ade08f4d7eed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987564"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;ensamblado&gt; elemento (aplicación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento de nivel superior para el manifiesto de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `assembly` es el elemento raíz y es necesario. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos del manifiesto deben estar en uno de los espacios de nombres siguientes:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 También deben ser elementos secundarios del ensamblado en estos espacios de nombres, mediante herencia o etiquetado.  
  
 El elemento `assembly` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`manifestVersion`|Obligatorio. El `manifestVersion` atributo debe establecerse en `1.0`.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se ilustra un `assembly` elemento en un manifiesto de aplicación para un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
```  
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
 [\<assembly> Element](../deployment/assembly-element-clickonce-deployment.md)
