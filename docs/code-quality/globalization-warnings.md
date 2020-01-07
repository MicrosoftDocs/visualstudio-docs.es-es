---
title: Advertencias de globalización
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fecc46ac6e1221cb547e98711d95b743010d4c6c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587581"
---
# <a name="globalization-warnings"></a>Advertencias de globalización
Las advertencias de globalización admiten aplicaciones y bibliotecas de uso internacional.

## <a name="in-this-section"></a>Esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1300: Especifique MessageBoxOptions](../code-quality/ca1300.md)|Para mostrar correctamente un cuadro de mensaje para las referencias culturales con escritura de derecha a izquierda, se deben pasar al método Show los miembros RightAlign y RtlReading de la enumeración MessageBoxOptions.|
|[CA1301: Evitar aceleradores duplicados](../code-quality/ca1301.md)|Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen claves de acceso duplicadas, el comportamiento de la tecla de acceso no está bien definido.|
|[CA1302: No codificar las cadenas específicas de configuración regional](../code-quality/ca1302.md)|La enumeración System.Environment.SpecialFolder contiene miembros que hacen referencia a carpetas del sistema especiales. La ubicación de estas carpetas puede tener diferentes valores en sistemas operativos distintos, el usuario puede cambiar alguna de estas ubicaciones y además, están adaptadas. El método Environment. GetFolderPath devuelve las ubicaciones que están asociadas a la enumeración Environment. SpecialFolder, localizada y adecuada para el equipo que se está ejecutando actualmente.|
|[CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303.md)|Un método visible externamente pasa un literal de cadena como un parámetro a un constructor o método .NET, y esa cadena debe ser localizable.|
|[CA1304: Especificar CultureInfo](../code-quality/ca1304.md)|Un método o constructor llama a un miembro que tiene una sobrecarga que acepta un parámetro System.Globalization.CultureInfo, y el método o constructor no llama a la sobrecarga que toma el parámetro CultureInfo. Si no se proporciona un objeto CultureInfo o System.IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1305: Especificar IFormatProvider](../code-quality/ca1305.md)|Un método o constructor llama a uno o más miembros que tienen sobrecargas que aceptan un parámetro System.IFormatProvider, y el método o constructor no llama a la sobrecarga que toma el parámetro IFormatProvider. Si no se proporciona un objeto System.Globalization.CultureInfo o IFormatProvider, el valor predeterminado proporcionado por el miembro sobrecargado podría no surtir el efecto deseado en todas las configuraciones regionales.|
|[CA1306: Establecer configuración regional para tipos de datos](../code-quality/ca1306.md)|La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para los valores numéricos, símbolos de divisa y criterio de ordenación. Cuando se crea un objeto DataTable o DataSet, debe establecerse explícitamente la configuración regional.|
|[CA1307: Especificar StringComparison](../code-quality/ca1307.md)|Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro StringComparison.|
|[CA1308: Normalizar las cadenas en mayúsculas](../code-quality/ca1308.md)|Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Hay un grupo pequeño de caracteres que no pueden realizar un viaje de ida y vuelta cuando se pasan a minúsculas.|
|[CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309.md)|Una operación no lingüística de comparación de cadenas no establece el parámetro StringComparison en Ordinal ni en OrdinalIgnoreCase. Si se establece explícitamente el parámetro en StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase, el código será más rápido y ganará en precisión y confiabilidad.|
|[CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101.md)|Un miembro de invocación de plataforma permite llamadores de confianza parcial, tiene un parámetro de cadena y no serializa explícitamente la cadena. Esto puede producir una vulnerabilidad de seguridad.|
