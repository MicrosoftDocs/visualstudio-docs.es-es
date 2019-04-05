---
title: 'CA1726: Utilizar términos preferidos | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "59003077"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1726: Utilizar términos preferidos](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) en docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|Identificador de comprobación|CA1726|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> No problemático: cuando se desencadena en los parámetros de tipo|  
  
## <a name="cause"></a>Motivo  
 El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. Como alternativa, el nombre incluye el término marca o marcas.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla analiza un identificador en tokens. Cada token único y cada combinación de dos tokens contiguos se comparan con los términos que se integra en la regla y en la sección en desuso de los diccionarios personalizados. La siguiente tabla muestra los términos que se integran en la regla y sus alternativas preferidas.  
  
|Término obsoleto|Término preferido|  
|-------------------|--------------------|  
|no es|AreNot|  
|Cancelado|Cancelado|  
|No se puede|No se puede|  
|ComPlus|EnterpriseServices|  
|No se pueden|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|No|DoNot|  
|Marca o indicadores|No hay ningún término de reemplazo. No utilizar.|  
|Hadnt|HadNot|  
|No se ha|HasNot|  
|todavía no|HaveNot|  
|Índices|Índices|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|no estaban|WereNot|  
|No|WillNot|  
|Wouldnt|WouldNot|  
|Puede escribir|Puede escribir|  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el término con el término preferido alternativo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla solo si el nombre del identificador es intencionado y se relaciona específicamente con el término original en lugar del término preferido.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)
