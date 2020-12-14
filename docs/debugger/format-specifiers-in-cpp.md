---
title: Especificadores de formato en el depurador (C++) | Microsoft Docs
description: Use un especificador de formato para cambiar el formato en el que se muestra un valor en las ventanas Inspección, Automático o Variables locales. En este artículo se proporcionan los detalles de uso.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 64166768dea1da015c223a74c74440ae09a0d106
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863041"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Especificadores de formato para C++ en el depurador de Visual Studio
Puede cambiar el formato en el que se muestra un valor en las ventanas **Inspección**, **Automático** y **Variables locales** mediante especificadores de formato.

También puede usar especificadores de formato en la ventana **Inmediato** y la ventana **Comando**, en [puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), e incluso en las ventanas de origen. Si hace una pausa sobre una expresión de esas ventanas, el resultado aparecerá en un cuadro desplegable de [información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). La visualización de información sobre datos refleja el especificador de formato.

> [!NOTE]
> Cuando el depurador nativo de Visual Studio cambia a un nuevo motor de depuración, se agregan algunos especificadores de formato nuevos y se quitan otros antiguos. El depurador antiguo todavía se usa cuando se realiza depuración de interoperabilidad (administrada y nativa mixta) con C++/CLI.

## <a name="set-format-specifiers"></a>Establecimiento de los especificadores de formato
Se usará el siguiente código de ejemplo:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Agregue la variable `my_var1` a la ventana **Inspección** al depurar, **Depurar** > **Ventanas** > **Inspección** > **Inspección 1**. Después, haga clic con el botón derecho en la variable y seleccione **Presentación hexadecimal**. Ahora, en la ventana **Inspección** se muestra el valor 0x0065. Para ver este valor expresado como un carácter en lugar de un entero, primero haga clic con el botón derecho y anule la selección de **Presentación hexadecimal**. Luego, agregue el especificador de formato de carácter **, c** en la columna **Nombre** después del nombre de la variable. En la columna **Valor** se muestra ahora **101 "e"** .

![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")

::: moniker range=">= vs-2019" 
Puede ver una lista de especificadores de formato disponibles y seleccionar de dicha lista anexando una coma (,) al valor de la ventana **Inspección**. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Especificadores de formato
En las siguientes tablas se describen los especificadores de formato que se pueden usar en Visual Studio. Los especificadores en negrita solo se admiten para el nuevo depurador y no para la depuración de interoperabilidad con C++/CLI.

::: moniker range=">= vs-2019" 

|Especificador|Formato|Valor de inspección original|Valor mostrado|
|---------------|------------|--------------------------|---------------------|
|d|Entero decimal|0x00000066|102|
|o|Entero octal sin signo|0x00000066|000000000146|
|x<br /><br /> **h**|entero hexadecimal|102|0xcccccccc|
|X<br /><br /> **H**|entero hexadecimal|102|0xcccccccc|
|xb<br /><br /> **hb**|entero hexadecimal (sin 0x inicial)|102|cccccccc|
|Xb<br /><br /> **Hb**|entero hexadecimal (sin 0x inicial)|102|CCCCCCCC|
|b|entero binario sin signo|25|0b00000000000000000000000000011001|
|bb|entero binario sin signo (sin 0b inicial)|25|00000000000000000000000000011001|
|h|notación científica|25000000|2.500000e+07|
|e|más corta, científica o de número de punto flotante|25000000|2.5e+07|
|c|carácter único|0x0065|101 'e'|
|s|const char* string (con comillas)|\<location> "hello world"|"hola a todos"|
|**sb**|Cadena const char* (sin comillas)|\<location> "hello world"|hola a todos|
|s8|Cadena UTF-8|\<location> "This is a UTF-8 coffee cup â˜•"|"This is a UTF-8 coffee cup ☕"|
|**s8b**|Cadena UTF-8 (sin comillas)|\<location> "hello world"|hola a todos|
|su|Cadena Unicode (codificación UTF-16) (con comillas)|\<location> L"hello world"|L"hola a todos"<br /><br /> u"hola a todos"|
|sub|Cadena Unicode (codificación UTF-16; sin comillas)|\<location> L"hello world"|hola a todos|
|bstr|Cadena binaria BSTR (con comillas)|\<location> L"hello world"|L"hola a todos"|
|env|Bloque de entorno (cadena terminada en doble null)|\<location> L"=::=::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Cadena UTF-32 (con comillas)|\<location> U"hello world"|u"hola a todos"|
|**s32b**|cadena UTF-32 (sin comillas)|\<location> U"hello world"|hola a todos|
|**en**|enum|Sábado(6)|Sábado|
|**hv**|Tipo de puntero: indica que el valor de puntero que se va a inspeccionar es el resultado de la asignación del montón de una matriz, por ejemplo, `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Suprime la dirección de memoria de un puntero a un objeto.|\<location>, {member=value...}|{member=value…}|
|**nd**|Muestra solo la información de la clase, omitiendo las clases derivadas|`(Shape*) square` incluye la información de clase base y derivada|Muestra únicamente la información de clase base|
|hr|HRESULT o código de error Win32. Este especificador ya no es necesario para los valores HRESULT dado que el depurador los descodifica automáticamente.|S_OK|S_OK|
|wc|Marcador de clase de ventana|0x0010|WC_DEFAULTCHAR|
|wm|Números de mensajes de Windows|16|WM_CLOSE|
|nr|Suprimir el elemento "Vista sin formato"|
|nvo|Mostrar el elemento "Vista sin formato" solo para valores numéricos|
|!|Sin formato, omite cualquier personalización de vistas de tipos de datos|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|Especificador|Formato|Valor de inspección original|Valor mostrado|
|---------------|------------|--------------------------|---------------------|
|d|Entero decimal|0x00000066|102|
|o|Entero octal sin signo|0x00000066|000000000146|
|x<br /><br /> **h**|entero hexadecimal|102|0xcccccccc|
|X<br /><br /> **H**|entero hexadecimal|102|0xcccccccc|
|c|carácter único|0x0065, c|101 'e'|
|s|const char* string (con comillas)|\<location> "hello world"|"hola a todos"|
|**sb**|Cadena const char* (sin comillas)|\<location> "hello world"|hola a todos|
|s8|Cadena UTF-8|\<location> "This is a UTF-8 coffee cup â˜•"|"This is a UTF-8 coffee cup ☕"|
|**s8b**|Cadena UTF-8 (sin comillas)|\<location> "hello world"|hola a todos|
|su|Cadena Unicode (codificación UTF-16) (con comillas)|\<location> L"hello world"|L"hola a todos"<br /><br /> u"hola a todos"|
|sub|Cadena Unicode (codificación UTF-16; sin comillas)|\<location> L"hello world"|hola a todos|
|bstr|Cadena binaria BSTR (con comillas)|\<location> L"hello world"|L"hola a todos"|
|env|Bloque de entorno (cadena terminada en doble null)|\<location> L"=::=::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Cadena UTF-32 (con comillas)|\<location> U"hello world"|u"hola a todos"|
|**s32b**|cadena UTF-32 (sin comillas)|\<location> U"hello world"|hola a todos|
|**en**|enum|Sábado(6)|Sábado|
|**hv**|Tipo de puntero: indica que el valor de puntero que se va a inspeccionar es el resultado de la asignación del montón de una matriz, por ejemplo, `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Suprime la dirección de memoria de un puntero a un objeto.|\<location>, {member=value...}|{member=value…}|
|**nd**|Muestra solo la información de la clase, omitiendo las clases derivadas|`(Shape*) square` incluye la información de clase base y derivada|Muestra únicamente la información de clase base|
|hr|HRESULT o código de error Win32. Este especificador ya no es necesario para los valores HRESULT dado que el depurador los descodifica automáticamente.|S_OK|S_OK|
|wc|Marcador de clase de ventana|0x0010|WC_DEFAULTCHAR|
|wm|Números de mensajes de Windows|16|WM_CLOSE|
|!|Sin formato, omite cualquier personalización de vistas de tipos de datos|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Cuando el especificador de formato **hv** está presente, el depurador intenta determinar la longitud del búfer y muestra el número apropiado de elementos. Dado que el depurador no siempre puede averiguar el tamaño del búfer exacto de una matriz, debe usar un especificador de tamaño de `(pBuffer,[bufferSize])` siempre que sea posible. El especificador de formato de **hv** es útil cuando el tamaño de búfer no está disponible fácilmente.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Especificadores de tamaño para punteros como matrices
Si tiene un puntero a un objeto que desea ver como una matriz, puede utilizar un entero o una expresión para especificar el número de elementos de matriz.

|Especificador|Formato|Valor de inspección original|Valor mostrado|
|---------------|------------|---------------------------|---------------------|
|n|Entero decimal o **hexadecimal**|pBuffer,[32]<br /><br /> pBuffer, **[0x20]**|Muestra `pBuffer` como una matriz de 32 elementos.|
|**[exp]**|Expresión de C++ válida que se evalúa como un entero.|pBuffer,[bufferSize]|Muestra pBuffer como una matriz de `bufferSize` elementos.|
|**expand(n)**|Expresión de C++ válida que se evalúa como un entero|pBuffer, expand(2)|Muestra el tercer elemento de  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Especificadores de formato para la depuración de interoperabilidad con C++/CLI
Los especificadores en **negrita** solo son compatibles con la depuración nativa y con el código C++/CLI.

|Especificador|Formato|Valor de inspección original|Valor mostrado|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|Entero decimal con signo|0xF000F065|-268373915|
|**u**|Entero decimal sin signo|0x0065|101|
|o|Entero octal sin signo|0xF065|0170145|
|x<br /><br />X|entero hexadecimal|61541|0x0000f065|
|**l**<br /><br />**h**|Prefijo long o short para: d, i, u, o, x, X|00406042|0x0c22|
|**f**|Punto flotante con signo|(3./2.), f|1.500000|
|**e**|Notación científica con signo|(3.0/2.0)|1.500000e+000|
|**g**|punto flotante con signo o notación científica con signo,<br/> lo que sea más corto|(3.0/2.0)|1.5|
|c|carácter único|\<location>|101 'e'|
|s|const char* (con comillas)|\<location>|"hola a todos"|
|su|const wchar_t*<br /><br /> const char16_t\* (con comillas)|\<location>|L"hola a todos"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hola a todos|
|s8|const char* (con comillas)|\<location>|"hola a todos"|
|hr|HRESULT o código de error Win32.<br/>Este especificador ya no es necesario para los valores HRESULT dado que el depurador los descodifica automáticamente.|S_OK|S_OK|
|wc|Marcador de clase de ventana|0x00000040,|WC_DEFAULTCHAR|
|wm|Números de mensajes de Windows|0x0010|WM_CLOSE|
|!|sin formato, omite cualquier personalización de vistas de tipos de datos|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Especificadores de formato para ubicaciones de memoria en la depuración de interoperabilidad con C++/CLI
En la siguiente tabla se describen los símbolos de formato que se utilizan en las ubicaciones de memoria. Puede utilizar un especificador de ubicación de memoria con cualquier valor o expresión que se evalúe como una ubicación.

|Símbolo|Formato|Valor de inspección original|Valor mostrado|
|------------|------------|--------------------------|---------------------|
|**ma**|64 caracteres ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|16 bytes en hexadecimal, seguidos de 16 caracteres ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mb**|16 bytes en hexadecimal, seguidos de 16 caracteres ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mw**|8 palabras|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 palabras dobles|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**mq**|2 palabras cuádruples|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|Caracteres de 2 bytes (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Especificador de tamaño para punteros como matrices en la depuración de interoperabilidad con C++/CLI
Si tiene un puntero a un objeto que desea ver como una matriz, puede utilizar un entero para especificar el número de elementos de matriz.

|Especificador|Formato|Expresión|Valor mostrado|
|---------------|------------|----------------|---------------------|
|n|Entero decimal|pBuffer[32]|Muestra `pBuffer` como una matriz de 32 elementos.|