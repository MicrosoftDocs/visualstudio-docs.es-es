---
title: 'CA1726: usar términos preferidos | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5d184684a6ec30c216b7274313905781843071b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671574"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1726: usar términos preferidos](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms).

|||
|-|-|
|TypeName|UsePreferredTerms|
|Identificador de comprobación|CA1726|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> Sin interrupción: cuando se desencadena en parámetros de tipo|

## <a name="cause"></a>Motivo
 El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. Como alternativa, el nombre incluye el término marca o marcas.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla analiza un identificador en tokens. Cada token único y cada combinación de token doble contigua se comparan con los términos que están integrados en la regla y en la sección desusada de cualquier diccionario personalizado. En la tabla siguiente se muestran los términos que están integrados en la regla y sus alternativas preferidas.

|Término obsoleto|Término preferido|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` o `Flags`|No hay ningún término de reemplazo. No utilizar.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el término por el término alternativo preferido.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo si el nombre del identificador es intencionado y está relacionado específicamente con el término original en lugar de con el término preferido.

## <a name="related-rules"></a>Reglas relacionadas
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)
