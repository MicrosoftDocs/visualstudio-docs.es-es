---
title: Dar formato a los especificadores en el depurador (C#) | Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe922960b0571593cc15581c29244798fd0f671e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018740"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato en C# en el depurador de Visual Studio
Puede cambiar el formato en el que se muestra un valor en el **inspección** ventana mediante el uso de especificadores de formato. También puede usar especificadores de formato en el **inmediato** ventana, el **comando** ventana, en [puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)y en las ventanas de código fuente. Si hace una pausa en una expresión de esas ventanas, el resultado aparecerá en un [información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) en la visualización del formato especificado.  
  
 Para usar un especificador de formato, escriba la expresión variable, seguida por una coma y el especificador adecuado.  
  
## <a name="set-format-specifiers"></a>Conjunto de especificadores de formato  
Vamos a usar el código de ejemplo siguiente:   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Agregar el `my_var1` variable a la **inspección** ventana durante la depuración, **depurar** > **Windows** > **ver**  >  **Inspección 1**. A continuación, haga clic en la variable y seleccione **presentación Hexadecimal**. Ahora el **inspección** ventana muestra el valor 0 x 0065. Para ver este valor como un entero decimal en lugar de como entero hexadecimal, agregue el especificador de formato decimal **, d.** en el **nombre** columna después del nombre de variable. El **valor** columna muestra ahora **101**.   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Especificadores de formato  
 La tabla siguiente se describen los C# especificadores para que el depurador de Visual Studio de formato.  
  
|Especificador|Formato|Valor de inspección original|Muestra|  
|---------------|------------|--------------------------|--------------|  
|ac|Forzar la evaluación de una expresión, que puede ser útil cuando se desactiva la evaluación implícita de propiedades y llamadas a función implícitas.|Mensaje “El usuario ha desactivado la evaluación de funciones implícita”|\<value>|  
|d|Entero decimal|0x0065|101|  
|dynamic|Muestra el objeto especificado mediante un vista dinámica|Muestra todos los miembros del objeto, incluida la vista dinámica|Muestra solo la vista dinámica|  
|h|Entero hexadecimal|61541|0x0000F065|  
|nq|cadena sin comillas|"Mi Cadena"|Mi Cadena|  
|nSe|Especifica el comportamiento de formato no. Evalúa la expresión "No tiene efectos secundarios". Si la expresión no se puede interpretar y solo se puede resolver con una evaluación (por ejemplo, una llamada de función), verá un error en su lugar.|N/D|N/D|
|hidden|Muestra todos los miembros públicos y no públicos|Muestra los miembros públicos|Muestra todos los miembros|  
|raw|Muestra el elemento tal como aparece en el nodo de elemento sin formato. Válido solo en objetos de servidor proxy.|Diccionario\<T >|Vista sin formato del diccionario\<T >|  
|results|Puede usar con una variable de un tipo que implementa IEnumerable o IEnumerable\<T >, normalmente es el resultado de una expresión de consulta. Solo muestra los miembros que contienen el resultado de la consulta.|Muestra todos los miembros|Muestra los miembros que cumplan las condiciones de la consulta|  
  
## <a name="see-also"></a>Vea también  
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Ventanas de variables locales y automáticas](../debugger/autos-and-locals-windows.md)
