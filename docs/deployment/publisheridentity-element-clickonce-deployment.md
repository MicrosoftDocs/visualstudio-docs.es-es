---
title: "Elemento &lt;publisherIdentity&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "publisherIdentity (elemento) [manifiesto de implementación ClickOnce], introducción"
  - "publisherIdentity (elemento) [manifiesto de implementación ClickOnce], sintaxis, elementos, y atributos"
  - "elemento necesario para los manifiestos firmados [ClickOnce], publisherIdentity (elemento)"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;publisherIdentity&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene información sobre el publicador que firmó este manifiesto de implementación.  
  
## Sintaxis  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Elementos y atributos  
 El elemento `publisherIdentity` es necesario para los manifiestos firmados.  En la tabla siguiente se muestran los atributos que admite el elemento `publisherIdentity`.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Obligatorio.  Describe la identidad del publicador de esta aplicación.|  
|`issuerKeyHash`|Obligatorio.  Contiene el hash SHA\-1 de la clave pública del emisor de certificado.|  
  
#### Parámetros  
  
## Valor de propiedad y valor devuelto  
  
## Excepciones  
  
## Comentarios  
  
## Requisitos  
  
## Subtítulo