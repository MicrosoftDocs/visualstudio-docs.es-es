---
title: 'CA1308: normalizar las cadenas a mayúsculas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538741"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar cadenas en mayúsculas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|NormalizeStringsToUppercase|
|Identificador de comprobación|CA1308|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una operación normaliza una cadena a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Un pequeño grupo de caracteres, cuando se convierten a minúsculas, no puede realizar un viaje de ida y vuelta. Realizar un viaje de ida y vuelta significa convertir los caracteres de una configuración regional a otra configuración regional que represente los datos de caracteres de forma diferente y, a continuación, recuperar con precisión los caracteres originales de los caracteres convertidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie las operaciones que convierten cadenas en minúsculas para que las cadenas se conviertan a mayúsculas en su lugar. Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir un mensaje de advertencia cuando no se toma la decisión de seguridad basada en el resultado (por ejemplo, cuando se muestra en la interfaz de usuario).

## <a name="see-also"></a>Consulte también
 [Advertencias de globalización](../code-quality/globalization-warnings.md)
