---
title: Reglas de globalización
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e046f7e885ea0a6002d07b6a06b6b3728bf607aa
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808644"
---
# <a name="globalization-rules"></a>Reglas de globalización
Las reglas de globalización admiten aplicaciones y bibliotecas de uso internacional.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303.md)|Un método visible externamente pasa un literal de cadena como un parámetro a un constructor o método .NET, y esa cadena debe ser localizable.|
|[CA1304: Especificar CultureInfo](../code-quality/ca1304.md)|Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro System.Globalization.CultureInfo, y el método o constructor no llama a la sobrecarga que toma el parámetro CultureInfo. Si no se proporciona un objeto CultureInfo o System.IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1305: Especificar IFormatProvider](../code-quality/ca1305.md)|Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un parámetro System.IFormatProvider, y el método o constructor no llama a la sobrecarga que toma el parámetro IFormatProvider. Si no se proporciona un objeto System.Globalization.CultureInfo o IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1306: Establecer configuración regional de tipos de datos](../code-quality/ca1306.md)|La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para los valores numéricos, símbolos de divisa y criterio de ordenación. Cuando se crea un objeto DataTable o DataSet, debe establecerse explícitamente la configuración regional.|
|[CA1307: Especificar StringComparison para mayor claridad](../code-quality/ca1307.md)|Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison.|
|[CA1308: Normalizar cadenas en mayúsculas](../code-quality/ca1308.md)|Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Hay un grupo pequeño de caracteres que no pueden realizar un viaje de ida y vuelta cuando se pasan a minúsculas.|
|[CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309.md)|Una operación no lingüística de comparación de cadenas no establece el parámetro StringComparison en Ordinal ni en OrdinalIgnoreCase. Si se establece explícitamente el parámetro en StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase, el código será más rápido y ganará en precisión y confiabilidad.|
|[CA1310: Especificar StringComparison para mayor corrección](../code-quality/ca1310.md)|Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison y utiliza de forma predeterminada la comparación de cadenas específica de la referencia cultural.|
|[CA2101: especificar el cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101.md)|Un miembro de invocación de plataforma permite llamadores de confianza parcial, tiene un parámetro de cadena y no serializa explícitamente la cadena. Esto puede producir una vulnerabilidad de seguridad.|
