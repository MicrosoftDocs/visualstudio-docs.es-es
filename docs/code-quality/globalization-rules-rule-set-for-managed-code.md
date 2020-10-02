---
title: Conjunto de reglas Reglas de globalización para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c3b899ec8e19160d9ee4a307a86c576d217004c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658547"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de globalización para código administrado

Utilice el conjunto de reglas reglas de globalización de Microsoft para centrarse en los problemas que podrían impedir que los datos de la aplicación aparezcan correctamente en diferentes idiomas, configuraciones regionales y referencias culturales. Debe incluir este conjunto de reglas si la aplicación está localizada, globalizada o ambas.

|Regla|Descripción|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|No pasar literales como parámetros localizados|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Especificar CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Especificar IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Especificar StringComparison para mayor claridad|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizar cadenas en mayúsculas|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Utilizar StringComparison ordinal|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Especificar StringComparison para la corrección|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Especificar serialización en argumentos de cadena P/Invoke|
