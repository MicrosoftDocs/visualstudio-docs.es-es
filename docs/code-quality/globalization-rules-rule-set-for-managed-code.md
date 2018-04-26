---
title: Conjunto de reglas Reglas de globalización para código administrado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5f260a46d26bfec8af61a39ba8c54910a45772c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de globalización para código administrado
Puede usar el conjunto que se centran en problemas que podrían evitar que los datos en la aplicación que aparezcan correctamente en diferentes idiomas, configuraciones regionales y referencias culturales de reglas reglas de globalización de Microsoft. Debe incluir este conjunto de reglas si la aplicación se localiza las globalizadas, o ambos.

|Regla|Descripción|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Especifique MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|No codificar las cadenas específicas de configuración regional|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|No pasar literales como parámetros localizados|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Especificar CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Especificar IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Establecer configuración regional para tipos de datos|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Especificar StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar las cadenas en mayúsculas|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Utilizar StringComparison ordinal|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique la serialización para argumentos de cadena P/Invoke|