---
title: "Configurar advertencias en Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errores [Visual Basic], advertencias"
  - "errores en tiempo de ejecución, advertencias"
  - "advertencias, configurar"
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configurar advertencias en Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] incluye un conjunto de advertencias sobre código que puede producir errores en tiempo de ejecución.  Puede utilizar esta información para escribir código más limpio, rápido y mejor con menos errores.  Por ejemplo, el compilador muestra una advertencia cuando el usuario intenta invocar un miembro de una variable de objeto sin asignar, volver de una función sin establecer el valor devuelto o ejecutar un bloque `Try` con errores en la lógica para detectar excepciones.  
  
 En ocasiones, el compilador proporciona lógica adicional en nombre del usuario para que éste pueda centrarse en la tarea actual en lugar de dedicarse a anticipar posibles errores.  En versiones anteriores de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], se utilizaba `Option Strict` para limitar la lógica adicional que proporciona el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  La configuración de las advertencias permite limitar esta lógica de una manera más específica, en el nivel de las advertencias individuales.  
  
 Puede personalizar su proyecto y desactivar algunas advertencias que no afectan a su aplicación o convertir otras advertencias en errores.  Esta página explica cómo activar y desactivar las advertencias individuales.  
  
## Activar y desactivar advertencias  
 Existen cuatro formas diferentes de configurar advertencias: puede configurarlas con el **Diseñador de proyectos** o puede utilizar las opciones de compilador **\/warnaserror** y **\/nowarn**.  
  
 La ficha **Compilar** de la página **Diseñador de proyectos** permite activar y desactivar las advertencias.  Active la casilla **Deshabilitar todas las advertencias** para deshabilitar todas las advertencias; active **Considerar todas las advertencias como errores** para tratar todas las advertencias como errores.  Algunas advertencias individuales se pueden alternar como errores o advertencias en la tabla mostrada.  
  
 Cuando **Option Strict** se establece como **Off**, las advertencias relacionadas con **Option Strict** no se pueden tratar como independientes entre sí.  Cuando **Option Strict** se establece como **On**, las advertencias asociadas se tratan como errores, independientemente de su estado.  Si **Option Strict** se establece como **Custom** mediante la especificación de `/optionstrict:custom` en el compilador de la línea de comandos, las advertencias de **Option Strict** se pueden activar y desactivar de manera independiente.  
  
 También se puede utilizar la opción de la línea de comandos **\/warnaserror** del compilador para especificar si las advertencias se tratan como errores.  Puede agregar una lista delimitada por comas a esta opción para especificar qué advertencias se deben tratar como errores o advertencias, utilizando \+ o \-.  En la tabla siguiente se especifican las opciones posibles.  
  
|Opción de la línea de comandos|Especifica|  
|------------------------------------|----------------|  
|`/warnaserror+`|Tratar todas las advertencias como errores|  
|`/warnsaserror`\-|No tratar las advertencias como errores.  Éste es el valor predeterminado.|  
|`/warnaserror+:<warning list` `>`|Tratar advertencias concretas como errores, indicadas por su número de identificador de error en una lista delimitada por comas.|  
|`/warnaserror-:<warning list>`|No tratar advertencias concretas como errores, indicadas por su número de identificador de error en una lista delimitada por comas.|  
|`/nowarn`|No indicar advertencias.|  
|`/nowarn:<warning list>`|No indicar advertencias concretas, indicadas por su número de identificador de error en una lista delimitada por comas.|  
  
 La lista de advertencias contiene el número de identificador de error de las advertencias que deben tratarse como errores, que se puede utilizar en las opciones de la línea de comandos para activar o desactivar advertencias concretas.  Si la lista de advertencias contiene un número no válido, se muestra un error.  
  
## Ejemplos  
 Esta tabla de ejemplos de argumentos de la línea de comandos describe qué hace cada argumento.  
  
|Argumento|Descripción|  
|---------------|-----------------|  
|`vbc /warnaserror`|Especifica que todas las advertencias se deben tratar como errores.|  
|`vbc /warnaserror:42024`|Especifica que la advertencia 42024 se debe tratar como un error.|  
|`vbc /warnaserror:42024,42025`|Especifica que las advertencias 42024 y 42025 se deben tratar como errores.|  
|`vbc /nowarn`|Especifica que no se deben indicar advertencias.|  
|`vbc /nowarn:42024`|Especifica que no se debe indicar la advertencia 42024.|  
|`vbc /nowarn:42024,42025`|Especifica que no se deben indicar las advertencias 42024 y 42025.|  
  
## Tipos de advertencias  
 A continuación se muestra una lista de advertencias que podría tratar como errores.  
  
### Advertencia de conversión implícita  
 Se genera para las instancias de conversión implícita.  No incluyen las conversiones implícitas de un tipo numérico intrínseco a una cadena cuando se utiliza el operador `&`.  Deshabilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42016  
  
### Advertencia de invocación de métodos enlazados en tiempo de ejecución y de resolución de sobrecarga  
 Se genera para las instancias de enlace en tiempo de ejecución.  Deshabilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42017  
  
### Advertencia de operandos de tipo Object  
 Se genera cuando se producen operandos de tipo `Object` que crearían un error con `Option Strict On`.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42018 y 42019  
  
### Advertencia de declaraciones que requieren la cláusula 'As'  
 Se genera cuando una declaración de variable, función o propiedad a la que le falta una cláusula `As` habría creado un error con `Option Strict On`.  Se supone que las variables que no tienen un tipo asignado son del tipo `Object`.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42020 \(declaración de variable\), 42021 \(declaración de función\) y 42022 \(declaración de propiedad\).  
  
### Advertencia de posible excepción de referencia NULL  
 Se genera cuando se utiliza una variable antes de ser asignada a un valor.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42104, 42030  
  
### Advertencia de variable local no usada  
 Se genera cuando se declara una variable local pero no se hace referencia a ella.  Habilitado de forma predeterminada.  
  
 ID: 42024  
  
### Advertencia de acceso a miembro Shared mediante una variable de instancia  
 Se genera cuando el acceso a un miembro Shared desde una instancia puede tener efectos secundarios o cuando el acceso a un miembro Shared desde una vista de instancia no constituye la parte derecha de una expresión o se pasa como un parámetro.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42025  
  
### Advertencia de acceso recursivo a un operador o una propiedad  
 Se genera cuando el cuerpo de una rutina usa el mismo operador o propiedad donde se ha definido.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42004 \(operador\), 42026 \(propiedad\)  
  
### Advertencia de función u operador sin valor devuelto  
 Se genera cuando la función o el operador no tiene un valor devuelto especificado.  Incluye la omisión de `Set` en la variable local implícita con el mismo nombre que la función.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42105 \(función\), 42016 \(operador\)  
  
### Advertencia de modificador Overloads utilizado en un módulo  
 Se genera cuando se utiliza `Overloads` en un objeto `Module`.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42028  
  
### Advertencia de bloques Catch duplicados o superpuestos  
 Se genera cuando no se alcanza un bloque `Catch` debido a su relación con otros bloques `Catch` definidos.  Habilitado de forma predeterminada para nuevos proyectos.  
  
 ID: 42029, 42031  
  
## Vea también  
 [Asistente de excepciones \(Cuadro de diálogo\)](../debugger/exception-assistant-dialog-box.md)   
 [Tipos de error](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)   
 [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)   
 [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Advertencias del compilador desactivadas de forma predeterminada](/visual-cpp/preprocessor/compiler-warnings-that-are-off-by-default)