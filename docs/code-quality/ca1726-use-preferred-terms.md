---
title: "CA1726: Utilizar t&#233;rminos preferidos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726: Utilizar t&#233;rminos preferidos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|Identificador de comprobación|CA1726|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> No problemático: cuando se desencadena en parámetros de tipo|  
  
## Motivo  
 El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado.  Alternativamente, el nombre incluye el término Flag o Flags.  
  
## Descripción de la regla  
 Esta regla analiza un identificador y lo desglosa en símbolos \(token\).  Cada token y cada combinación dual de tokens contiguos se compara con los términos incorporados a la regla y contenidos en la sección de términos desusados de los diccionarios personalizados.  La tabla siguiente muestra los términos incorporados en la regla y sus alternativas preferidas.  
  
|Término obsoleto|Término preferido|  
|----------------------|-----------------------|  
|Arent|AreNot|  
|Cancelado|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag o Flags|No hay ninguna condición de colocación.  No utilizar.|  
|Hadnt|HadNot|  
|Hasn’t|HasNot|  
|Havent|HaveNot|  
|Indices|Índices|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el término por el término alternativo preferido.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla únicamente si el nombre del identificador se asignó de forma intencionada y está relacionado específicamente con el término original, no con el término preferido.  
  
## Reglas relacionadas  
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)