---
title: Advertencias de globalización
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2c72bc2942040bc76f6e43821b3257e424e30de
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="globalization-warnings"></a>Advertencias de globalización
Advertencias de globalización son compatibles con las aplicaciones y bibliotecas de uso internacional.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1300: Especifique MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Para mostrar correctamente un cuadro de mensaje para las referencias culturales con escritura de derecha a izquierda, se deben pasar al método Show los miembros RightAlign y RtlReading de la enumeración MessageBoxOptions.|
|[CA1301: Evitar aceleradores duplicados](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen las teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso.|
|[CA1302: No codificar las cadenas específicas de configuración regional](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|La enumeración System.Environment.SpecialFolder contiene miembros que hacen referencia a carpetas del sistema especiales. La ubicación de estas carpetas puede tener diferentes valores en sistemas operativos distintos, el usuario puede cambiar alguna de estas ubicaciones y además, están adaptadas. El método Environment.GetFolderPath devuelve las ubicaciones asociadas a la enumeración Environment.SpecialFolder, adaptadas y adecuadas al equipo actualmente en ejecución.|
|[CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Un método visible externamente analiza un literal de cadena como parámetro para un constructor o método de la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y esa cadena debería ser localizable.|
|[CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro System.Globalization.CultureInfo, y el método o constructor no llama a la sobrecarga que toma el parámetro CultureInfo. Si no se proporciona un objeto CultureInfo o System.IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1305: Especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un parámetro System.IFormatProvider, y el método o constructor no llama a la sobrecarga que toma el parámetro IFormatProvider. Si no se proporciona un objeto System.Globalization.CultureInfo o IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1306: Establecer configuración regional para tipos de datos](../code-quality/ca1306-set-locale-for-data-types.md)|La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para los valores numéricos, símbolos de divisa y criterio de ordenación. Cuando se crea un objeto DataTable o DataSet, debe establecerse explícitamente la configuración regional.|
|[CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison.|
|[CA1308: Normalizar las cadenas en mayúsculas](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Hay un grupo pequeño de caracteres que no pueden realizar un viaje de ida y vuelta cuando se pasan a minúsculas.|
|[CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Una operación no lingüística de comparación de cadenas no establece el parámetro StringComparison en Ordinal ni en OrdinalIgnoreCase. Si se establece explícitamente el parámetro en StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase, el código será más rápido y ganará en precisión y confiabilidad.|
|[CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Una invocación de plataforma permite llamadores parcialmente confiables, miembro tiene un parámetro de cadena y no serializa explícitamente la cadena. Esto puede producir una vulnerabilidad de seguridad.|