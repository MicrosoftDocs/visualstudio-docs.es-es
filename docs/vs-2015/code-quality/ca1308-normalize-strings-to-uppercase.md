---
title: 'CA1308: Normalizar las cadenas en mayúsculas | Microsoft Docs'
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
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8f5a40d412b8ea9616dd75d7e0424ba447b5a185
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47583262"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar las cadenas en mayúsculas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1308: normalizar las cadenas a mayúsculas](https://docs.microsoft.com/visualstudio/code-quality/ca1308-normalize-strings-to-uppercase).

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|Identificador de comprobación|CA1308|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una operación normaliza una cadena a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Un pequeño grupo de caracteres al que se convierten a minúsculas, no se puede realizar un recorrido de ida y. Para realizar un recorrido de ida y medios para convertir los caracteres de una configuración regional para otra configuración regional que representa datos de caracteres de forma diferente y, a continuación, con precisión recuperan los caracteres originales de los caracteres convertidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambiar las operaciones que convierten cadenas a minúscula para que las cadenas se convierten a mayúsculas en su lugar. Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir un mensaje de advertencia cuando no estás realizando la decisión de seguridad en función del resultado (por ejemplo, cuando se muestran en la interfaz de usuario).

## <a name="see-also"></a>Vea también
 [Advertencias de globalización](../code-quality/globalization-warnings.md)



