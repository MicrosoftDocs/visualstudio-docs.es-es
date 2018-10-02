---
title: 'CA1726: Utilizar términos preferidos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: b13c43a563a158a2eeb8484e29810c5b91d110aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567596"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [CA1726: utilizar términos preferidos](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) en docs.microsoft.com.  
  
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
|no es|No van|  
|Cancelado|Cancelado|  
|No se puede|No se puede|  
|ComPlus|EnterpriseServices|  
|No se pueden|CouldNot|  
|Didnt|DidNot|  
|Doesnt|No|  
|No|No conectar|  
|Marca o indicadores|No hay ningún término de reemplazo. No utilizar.|  
|no se habían|HadNot|  
|No se ha|HasNot|  
|todavía no|HaveNot|  
|Índices|Índices|  
|no es|IsNot|  
|Inicio de sesión|Inicio de sesión|  
|Cierre de sesión|Cierre de sesión|  
|Shouldnt|ShouldNot|  
|Inicio de sesión|Inicio de sesión|  
|Aprobación|Cierre de sesión|  
|Wasnt|WasNot|  
|no estaban|No están|  
|No|No|  
|Wouldnt|WouldNot|  
|Puede escribir|Puede escribir|  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el término con el término preferido alternativo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla solo si el nombre del identificador es intencionado y se relaciona específicamente con el término original en lugar del término preferido.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)

