---
title: "Elemento &lt;compatibleFrameworks&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<compatibleFrameworks> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;compatibleFrameworks&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica las versiones de .NET Framework donde se puede instalar y ejecutar esta aplicación.  
  
> [!NOTE]
>  [MageUI.exe](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md) no admite el elemento de `compatibleFrameworks` al guardar un manifiesto de aplicación que se ha firmado ya con un certificado mediante [MageUI.exe](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  En su lugar, debe utilizar [Mage.exe](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## Sintaxis  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## Elementos y atributos  
 El elemento `compatibleFrameworks` es necesario para los manifiestos de implementación orientados al runtime de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que proporciona [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o posterior.  El elemento `compatibleFrameworks` contiene uno o más elementos `framework` que especifican las versiones de .NET Framework en las que se puede ejecutar esta aplicación.  El runtime de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ejecutará la aplicación en el primer elemento `framework` disponible de esta lista.  
  
 En la tabla siguiente se enumeran los atributos que admite el elemento `compatibleFrameworks`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`S` `upportUrl`|Opcional.  Especifica una dirección URL donde se puede descargar la versión compatible de .NET Framework más adecuada.|  
  
## framework  
 Obligatorio.  En la tabla siguiente se enumeran los atributos que admite el elemento `framework`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`targetVersion`|Obligatorio.  Especifica el número de versión de .NET Framework de destino.|  
|`profile`|Obligatorio.  Especifica el perfil de .NET Framework de destino.|  
|`supportedRuntime`|Obligatorio.  Especifica el número de versión del runtime asociado a .NET Framework de destino.|  
  
## Comentarios  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `compatibleFrameworks` en un manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Esta implementación se puede ejecutar en [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  También se puede ejecutar en [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] porque es un supraconjunto de [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)