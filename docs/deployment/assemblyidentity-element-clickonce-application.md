---
title: "Elemento &lt;assemblyIdentity&gt; (Aplicaci&#243;n ClickOnce) | Microsoft Docs"
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
  - "<assemblyIdentity> (elemento) [manifiesto de aplicación ClickOnce]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;assemblyIdentity&gt; (Aplicaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica la aplicación implementada en una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Sintaxis  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `assemblyIdentity`.  No contiene ningún elemento secundario y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Obligatorio.  Identifica el nombre de la aplicación.<br /><br /> Si `Name` contiene caracteres especiales, como comillas dobles o sencillas, la aplicación podría no activarse.|  
|`Version`|Obligatorio.  Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|  
|`publicKeyToken`|Opcional.  Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes del valor hash `SHA-1` de la clave pública bajo la que se firma la aplicación o el ensamblado.  La clave pública que se utiliza para firmar el catálogo debe tener 2048 bits o más.<br /><br /> Aunque la firma del ensamblado es opcional \(pero recomendable\), este atributo es obligatorio.  Si un ensamblado no tiene firma, debe copiar un valor de un ensamblado autofirmado o utilizar un valor "ficticio" compuesto de ceros.|  
|`processorArchitecture`|Obligatorio.  Especifica el procesador.  Los valores válidos son `msil` para todos los procesadores, `x86` para Windows de 32 bits, `IA64` para Windows de 64 bits e `Itanium` para procesadores Intel Itanium de 64 bits.|  
|`language`|Obligatorio.  Identifica los códigos de idioma de dos partes \(por ejemplo, `en-US`\) del ensamblado.  Este elemento se encuentra en el espacio de nombres `asmv2`.  Si no se especifica, el valor predeterminado es `neutral`.|  
  
## Ejemplos  
  
### Descripción  
 En el siguiente ejemplo de código se muestra un elemento `assemblyIdentity` en un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### Código  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-deployment.md)