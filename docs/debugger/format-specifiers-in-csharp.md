---
title: "Especificadores de formato en C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "CSharp"
helpviewer_keywords: 
  - "depurador, especificadores de formato reconocidos"
  - "expresiones [C#], aplicar formato a valores"
  - "especificadores de formato, depurador"
  - "Inspección rápida (cuadro de diálogo), especificadores de formato en C#"
  - "Inspección rápida (cuadro de diálogo), utilizar especificadores de formato"
  - "especificadores"
  - "especificadores, formato de variables de inspección"
  - "símbolos, aplicar formato a variables de inspección"
  - "variables [depurador], símbolos de variables de inspección"
  - "símbolos de variables de inspección"
  - "Inspección (ventana), especificadores de formato en C#"
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Especificadores de formato en C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede cambiar el formato en el que se muestra un valor en la ventana **Inspección** mediante especificadores de formato. También puede usar especificadores de formato en las ventanas **Inmediato** y **Comandos**, así como en las ventanas de código fuente. Si hace una pausa sobre una expresión de esas ventanas, el resultado aparecerá en un cuadro desplegable de información sobre datos. Estos cuadros mostrarán el especificador de formato en la pantalla de información sobre datos.  
  
 Para utilizar un especificador de formato, escriba la expresión seguida de una coma. Tras la coma, agregue el especificador adecuado.  
  
## Uso de especificadores de formato  
 Si tiene el siguiente código:  
  
```  
{ int my_var1 = 0x0065; int my_var2 = 0x0066; int my_var3 = 0x0067; }  
```  
  
 Agregue la variable `my_var1` a la ventana Inspección \(durante la depuración, **Debug \/ Windows \/ Watch \/ Watch 1**\) y establezca la visualización en formato hexadecimal \(en la ventana **Inspección**, haga clic en la variable y seleccione **Presentación hexadecimal**\). Ahora la ventana **Inspección** muestra que contiene el valor 0x0065. Para ver el valor expresado como entero decimal en lugar de como entero hexadecimal, en la columna Nombre, agregue el especificador de formato de carácter **, d**. La columna Valor muestra ahora el valor decimal 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## Especificadores de formato  
 La siguiente tabla muestra los especificadores de formato de C\# que reconoce el depurador.  
  
|Especificador|Formato|Valor de inspección original|Muestra|  
|-------------------|-------------|----------------------------------|-------------|  
|ac|Fuerza la evaluación de una expresión. Esto puede resultar útil si se desactiva la evaluación implícita de propiedades y las llamadas a funciones implícitas. Vea [Expresiones y efectos secundarios](../Topic/Side%20Effects%20and%20Expressions.md).|Mensaje “El usuario ha desactivado la evaluación de funciones implícita”|\<valor\>|  
|d|Entero decimal|0x0065|101|  
|dynamic|Muestra el objeto especificado mediante un vista dinámica|Muestra todos los miembros del objeto, incluida la vista dinámica|Muestra solo la vista dinámica|  
|h|Entero hexadecimal|61541|0x0000F065|  
|nq|cadena sin comillas|"Mi Cadena"|Mi Cadena|  
|hidden|Muestra todos los miembros públicos y no públicos|Muestra los miembros públicos|Muestra todos los miembros|  
|raw|Muestra el elemento tal como aparece en el nodo de elemento sin formato. Válido solo en objetos de servidor proxy.|Dictionary\<T\>|Vista sin formato de Dictionatry\<T\>|  
|results|Se utiliza con una variable de un tipo que implementa IEnumerable o IEnumerable\<T\>, que normalmente es el resultado de una expresión de consulta. Solo muestra los miembros que contienen el resultado de la consulta.|Muestra todos los miembros.|Muestra los miembros que cumplan las condiciones de la consulta.|  
  
## Vea también  
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Ventanas de variables](../Topic/Variable%20Windows.md)