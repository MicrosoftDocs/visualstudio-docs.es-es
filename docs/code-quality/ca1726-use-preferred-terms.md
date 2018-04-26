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
ms.openlocfilehash: b4f83e7754bcb96de05eac3273133cabbc8b8f61
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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