---
title: 'CA1726: Utilizar términos preferidos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c81bd543a6695adcea37db5ab8570ff7749c0160
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551459"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos

|||
|-|-|
|TypeName|UsePreferredTerms|
|Identificador de comprobación|CA1726|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> No problemático: cuando se desencadena en los parámetros de tipo|

## <a name="cause"></a>Motivo

El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. O bien, el nombre incluye el término marca o marcas.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza un identificador en tokens. Cada token único y cada combinación de dos tokens contiguos se comparan con los términos que se integra en la regla y en la sección en desuso de los diccionarios personalizados. La siguiente tabla muestra los términos que se integran en la regla y sus alternativas preferidas.

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
 Para corregir una infracción de esta regla, reemplace el término con el término preferido alternativo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla solo si el nombre del identificador es intencionado y se relaciona específicamente con el término original en lugar del término preferido.

## <a name="related-rules"></a>Reglas relacionadas
 [Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)