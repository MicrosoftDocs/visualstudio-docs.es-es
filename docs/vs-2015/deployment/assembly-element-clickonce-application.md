---
title: '&lt;elemento Assembly &gt; (aplicación ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183480"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly &gt; (elemento, aplicación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El elemento de nivel superior para el manifiesto de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 El `assembly` elemento es el elemento raíz y es obligatorio. Su primer elemento contenido debe ser un `assemblyIdentity` elemento. Los elementos de manifiesto deben estar en uno de los siguientes espacios de nombres:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Los elementos secundarios del ensamblado también deben estar en estos espacios de nombres, por herencia o mediante el etiquetado.  
  
 El elemento `assembly` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`manifestVersion`|Necesario. El `manifestVersion` atributo debe establecerse en `1.0` .|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un `assembly` elemento en un manifiesto de aplicación para una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en el [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<assembly>](../deployment/assembly-element-clickonce-deployment.md)
