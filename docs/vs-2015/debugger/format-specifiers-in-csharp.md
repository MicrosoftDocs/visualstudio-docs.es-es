---
title: Format Specifiers in C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3521f39227b5abcb51a4db6b61e6bf0d853e5afe
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2019
ms.locfileid: "59002301"
---
# <a name="format-specifiers-in-c"></a>Especificadores de formato en C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cambiar el formato en el que se muestra un valor en la ventana **Inspección** mediante especificadores de formato. También puede usar especificadores de formato en las ventanas **Inmediato** y **Comandos** , así como en las ventanas de código fuente. Si hace una pausa sobre una expresión de esas ventanas, el resultado aparecerá en un cuadro desplegable de información sobre datos. Estos cuadros mostrarán el especificador de formato en la pantalla de información sobre datos.  
  
 Para utilizar un especificador de formato, escriba la expresión seguida de una coma. Tras la coma, agregue el especificador adecuado.  
  
## <a name="using-format-specifiers"></a>Uso de especificadores de formato  
 Si tiene el siguiente código:  
  
```  
{  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Agregue la variable `my_var1` a la ventana Inspección (durante la depuración, **Debug / Windows / Watch / Watch 1**) y establezca la visualización en formato hexadecimal (en la ventana **Inspección** , haga clic en la variable y seleccione **Presentación hexadecimal**). Ahora la ventana **Inspección** muestra que contiene el valor 0x0065. Para ver el valor expresado como entero decimal en lugar de como entero hexadecimal, en la columna Nombre, agregue el especificador de formato de carácter **, d**. La columna Valor muestra ahora el valor decimal 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Especificadores de formato  
 La siguiente tabla muestra los especificadores de formato de C# que reconoce el depurador.  
  
|Especificador|Formato|Valor de inspección original|Muestra|  
|---------------|------------|--------------------------|--------------|  
|ac|Fuerza la evaluación de una expresión. Esto puede resultar útil si se desactiva la evaluación implícita de propiedades y las llamadas a funciones implícitas. Vea [Side Effects and Expressions](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Mensaje “El usuario ha desactivado la evaluación de funciones implícita”|\<value>|  
|d|Entero decimal|0x0065|101|  
|dynamic|Muestra el objeto especificado mediante un vista dinámica|Muestra todos los miembros del objeto, incluida la vista dinámica|Muestra solo la vista dinámica|  
|h|Entero hexadecimal|61541|0x0000F065|  
|nq|cadena sin comillas|"Mi Cadena"|Mi Cadena|  
|hidden|Muestra todos los miembros públicos y no públicos|Muestra los miembros públicos|Muestra todos los miembros|  
|raw|Muestra el elemento tal como aparece en el nodo de elemento sin formato. Válido solo en objetos de servidor proxy.|Diccionario\<T >|Vista sin formato del diccionario\<T >|  
|results|Puede usar con una variable de un tipo que implementa IEnumerable o IEnumerable\<T >, normalmente es el resultado de una expresión de consulta. Solo muestra los miembros que contienen el resultado de la consulta.|Muestra todos los miembros.|Muestra los miembros que cumplan las condiciones de la consulta.|  
  
## <a name="see-also"></a>Vea también  
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Ventanas de variables](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
