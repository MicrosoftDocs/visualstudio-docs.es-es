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
  - "<assembly> (elemento) [manifiesto de aplicación ClickOnce]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento de nivel superior del manifiesto de aplicación.  
  
## Sintaxis  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Elementos y atributos  
 El elemento `assembly` es el elemento raíz y es necesario.  Su primer elemento contenido debe ser un elemento `assemblyIdentity`.  Los elementos del manifiesto deben estar en uno de los espacios de nombres siguientes:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Los elementos secundarios del ensamblado también deben estar en estos espacios de nombres, mediante herencia o etiquetas.  
  
 El elemento `assembly` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`manifestVersion`|Obligatorio.  El atributo `manifestVersion` debe establecerse en `1.0`.|  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestran un elemento `assembly` de un manifiesto de aplicación para una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
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
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<assembly\>](../deployment/assembly-element-clickonce-deployment.md)