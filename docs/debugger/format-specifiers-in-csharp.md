---
title: Especificadores de formato en el depurador (C#) | Microsoft Docs
description: Use un especificador de formato para cambiar el formato en el que se muestra un valor en la ventana Inspección. En este artículo se proporcionan los detalles de uso.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: abc824cf5d0413f01ad5f3f4423b974aeca40b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870589"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato en C# en el depurador de Visual Studio
Puede cambiar el formato en el que se muestra un valor en la ventana **Inspección** mediante especificadores de formato. También puede usar especificadores de formato en la ventana **Inmediato** y la ventana **Comando**, en [puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) y en ventanas de código fuente. Si realiza una pausa sobre una expresión de esas ventanas, el resultado aparecerá en una [información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) en el formato de presentación especificado.

Para usar un especificador de formato, escriba la expresión de variable seguida de una coma y el especificador adecuado.

## <a name="set-format-specifiers"></a>Establecimiento de especificadores de formato
Se usará el siguiente código de ejemplo:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Agregue la variable `my_var1` a la ventana **Inspección** al depurar, **Depurar** > **Ventanas** > **Inspección** > **Inspección 1**. Después, haga clic con el botón derecho en la variable y seleccione **Presentación hexadecimal**. Ahora, en la ventana **Inspección** se muestra el valor 0x0065. Para ver este valor como un entero decimal en lugar de un entero hexadecimal, agregue el especificador de formato decimal **, d** en la columna **Nombre** después del nombre de la variable. En la columna **Valor** ahora se muestra **101**.

![Captura de pantalla de la ventana Inspección de Visual Studio con una línea que muestra "my_var1, d" con un valor de "101" y un tipo "int".](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

Puede ver una lista de especificadores de formato disponibles y seleccionar en esa lista mediante la anexión de una coma (,) al valor de la ventana **Inspección**. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Especificadores de formato
En la tabla siguiente se describen los especificadores de formato de C# para el depurador de Visual Studio.

|Especificador|Formato|Valor de inspección original|Muestra|
|---------------|------------|--------------------------|--------------|
|ac|Se fuerza la evaluación de una expresión, lo que puede resultar útil si se desactiva la evaluación implícita de propiedades y las llamadas a funciones implícitas.|Mensaje “El usuario ha desactivado la evaluación de funciones implícita”|\<value>|
|d|Entero decimal|0x0065|101|
|dynamic|Muestra el objeto especificado mediante un vista dinámica|Muestra todos los miembros del objeto, incluida la vista dinámica|Muestra solo la vista dinámica|
|h|Entero hexadecimal|61541|0x0000F065|
|nq|cadena sin comillas|"Mi Cadena"|Mi Cadena|
|nse|Especifica el comportamiento, no el formato. Evalúa la expresión con "Sin efectos secundarios". Si la expresión no se puede interpretar y solo se puede resolver mediante una evaluación (por ejemplo, una llamada de función), verá un error en su lugar.|N/D|N/D|
|hidden|Muestra todos los miembros públicos y no públicos|Muestra los miembros públicos|Muestra todos los miembros|
|raw|Muestra el elemento tal como aparece en el nodo de elemento sin formato. Válido solo en objetos de servidor proxy.|Diccionario\<T>|Vista sin formato de Dictionary\<T>|
|results|Se usa con una variable de un tipo que implementa IEnumerable o IEnumerable\<T>, que normalmente es el resultado de una expresión de consulta. Solo muestra los miembros que contienen el resultado de la consulta.|Muestra todos los miembros|Muestra los miembros que cumplan las condiciones de la consulta|

## <a name="see-also"></a>Vea también
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Ventanas de variables locales y automáticas](../debugger/autos-and-locals-windows.md)
