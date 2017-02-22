---
title: "Elemento &lt;assemblyIdentity&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assemblyIdentity&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica el ensamblado primario de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Sintaxis  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `assemblyIdentity`.  No contiene ningún elemento secundario y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio.  Identifica el nombre descriptivo de la implementación con propósitos informativos.<br /><br /> Si `name` contiene caracteres especiales, como comillas dobles o sencillas, la aplicación podría no activarse.|  
|`version`|Obligatorio.  Especifica el número de versión del ensamblado con el formato siguiente: `principal.secundaria.compilación.revisión`.<br /><br /> Este valor se debe incrementar en un manifiesto actualizado para desencadenar una actualización de la aplicación.|  
|`publicKeyToken`|Obligatorio.  Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash SHA\-1 de la clave pública bajo la que se firma el manifiesto de implementación.  La clave pública que se utiliza para firmar debe tener 2048 bits o más.<br /><br /> Aunque la firma del ensamblado es opcional \(pero recomendable\), este atributo es obligatorio.  Si un ensamblado no tiene firma, debe copiar un valor de un ensamblado autofirmado o utilizar un valor "ficticio" compuesto de ceros.|  
|`processorArchitecture`|Obligatorio.  Especifica el procesador.  Los valores válidos son `msil` para todos los procesadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits e `Itanium` para procesadores Intel Itanium de 64 bits.|  
|`type`|Obligatorio.  Por razones de compatibilidad con la tecnología de instalación en paralelo de Windows.  El único valor permitido es `win32`.|  
  
## Comentarios  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `assemblyIdentity` en un manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)