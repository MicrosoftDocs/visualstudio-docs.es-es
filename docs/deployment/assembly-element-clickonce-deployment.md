---
title: "&lt;assembly&gt; (Elemento) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;assembly&gt; (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento de nivel superior del manifiesto de implementación.  
  
## Sintaxis  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Elementos y atributos  
 El elemento `assembly` es el elemento raíz y es necesario.  Su primer elemento contenido debe ser un elemento `assemblyIdentity`.  Los elementos de manifiesto deben estar en los siguientes espacios de nombres: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2` y `http://www.w3.org/2000/09/xmldsig#`.  Los elementos secundarios del ensamblado también deben estar en estos espacios de nombres, mediante herencia o etiquetas.  
  
 El elemento `assembly` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`manifestVersion`|Obligatorio.  Este atributo debe establecerse en `1.0`.|  
  
## Ejemplo  
 En el siguiente ejemplo de código se ilustra un elemento `assembly` en un manifiesto de implementación para una aplicación implementada utilizando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
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
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md)