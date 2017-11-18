---
title: "CA1726: Utilizar términos preferidos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|Identificador de comprobación|CA1726|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> Poco problemático: cuando se desencadena en parámetros de tipo|  
  
## <a name="cause"></a>Motivo  
 El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. O bien, el nombre incluye el término Flag o Flags.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla analiza un identificador en tokens. Cada token único y cada combinación de dos tokens contiguos se comparan con los términos que se integra en la regla y en la sección en desuso de los diccionarios personalizados. La siguiente tabla muestra los términos que se integran en la regla y sus alternativas preferidas.  
  
|Término obsoleto|Término preferido|  
|-------------------|--------------------|  
|no es|No van|  
|Cancelado|Cancelado|  
|No se puede|No se puede|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|No|  
|No|No|  
|Flag o Flags|No hay ningún término de reemplazo. No utilizar.|  
|no se había|HadNot|  
|No se ha|HasNot|  
|no ha|HaveNot|  
|Índices|Índices|  
|no es|IsNot|  
|Inicio de sesión|Inicio de sesión|  
|Cierre de sesión|Cierre de sesión|  
|Shouldnt|ShouldNot|  
|Inicio de sesión|Inicio de sesión|  
|Firma|Cierre de sesión|  
|Wasnt|WasNot|  
|no|No están|  
|Produce|No|  
|Wouldnt|WouldNot|  
|Puede escribir|Puede escribir|  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el término por el término alternativo preferido.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla sólo si el nombre del identificador es deliberado y relacionada específicamente con el término original en lugar del término preferido.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)