---
title: "&lt;description&gt; (Elemento) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;description&gt; (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica información de la aplicación usada para crear una presencia de shell y un elemento **Agregar o quitar programas** en el Panel de control.  
  
## Sintaxis  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `description`, que se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1`.  No contiene ningún elemento secundario y tiene los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`publisher`|Obligatorio.  Identifica el nombre de la empresa utilizado para la colocación de iconos en el menú **Inicio** de Windows y en el elemento **Agregar o quitar programas** del Panel de control, cuando se configura la implementación para la instalación.|  
|`product`|Obligatorio.  Identifica el nombre completo del producto.  Se utiliza como título para el icono instalado en el menú **Inicio** de Windows.|  
|`suiteName`|Opcional.  Identifica una subcarpeta dentro de la carpeta `publisher` en el menú **Inicio** de Windows.|  
|`supportUrl`|Opcional.  Especifica una dirección URL de soporte mostrada en el elemento **Agregar o quitar programas** en el Panel de control.  También se crea un acceso directo a esta dirección URL para el soporte de aplicaciones en el menú **Inicio** de Windows, cuando la implementación se configura para la instalación.|  
  
## Comentarios  
 El elemento de descripción es necesario en todas las configuraciones de la implementación.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra un elemento `description` en un manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)