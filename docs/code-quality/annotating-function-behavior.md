---
title: "Anotar el comportamiento de funciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Anotar el comportamiento de funciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Además de tener en cuenta [parámetros y valores devueltos de la función](../code-quality/annotating-function-parameters-and-return-values.md), puede anotar las propiedades de la función de conjunto.  
  
## Anotaciones de función  
 Las anotaciones siguientes se aplican a la función en conjunto y se describe cómo se comporta o lo que espera sean true.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Called_from_function_class_(name)`|No previsto son sólo; en su lugar, es un predicado que se utilizará con anotaciones de `_When_` .  Para obtener más información, vea [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> El parámetro de `name` es una cadena arbitraria que también aparece en una anotación de `_Function_class_` en la declaración de algunas funciones.  `_Called_from_function_class_` devuelve cero si la función que se está analizando actualmente se anota utilizando `_Function_class_` que tiene el mismo valor de `name`; de lo contrario, devuelve cero.|  
|`_Check_return_`|Indica un valor devuelto y los estados que el llamador debe inspeccionarlo.  Los informes de comprobación un error si se llama a la función en un contexto vacío.|  
|`_Function_class_(name)`|El parámetro de `name` es una cadena arbitraria notificada por el usuario.  Existe en un espacio de nombres que es distinto de otros espacios de nombres.  Una función, un puntero a función, o \- más un tipo de puntero a función de usefully\-a se pueden designar como pertenecientes a una o más clases de la función.|  
|`_Raises_SEH_exception_`|Observe una función que genera siempre una excepción estructurada de \(SEH\) de controlador de excepciones, sujeto a `_When_` y condiciones de `_On_failure_` .  Para obtener más información, vea [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Observe una función que pueda activar opcionalmente una excepción de SEH, sujeto a `_When_` y condiciones de `_On_failure_` .|  
|`_Must_inspect_result_`|Anota cualquier valor de salida, incluido el valor devuelto, los parámetros y las globales.  Los informes del analizador un error si el valor del objeto anotado no se inspecciona posteriormente. “Examinar” incluye si se utiliza en una expresión condicional, asignado a un parámetro de salida o global, o se pasa como parámetro.  Para los valores devueltos, `_Must_inspect_result_` implica `_Check_return_`.|  
|`_Use_decl_annotations_`|Se puede utilizar en una definición de función \(también conocida como cuerpo de función\) en lugar de la lista de anotaciones en el encabezado.  Cuando se utiliza `_Use_decl_annotations_` , se utilizan las anotaciones que aparecen en un encabezado de en\- ámbito para la misma función que si también están presentes en la definición que tiene la anotación de `_Use_decl_annotations_` .|  
  
## Anotaciones correctas\/erróneas  
 Una función puede producir un error, y cuando lo haga, los resultados pueden ser incompletos o diferir de los resultados a la función correctamente.  Las anotaciones en la lista siguiente proporcionan maneras de expresar el comportamiento de error.  Para utilizar estas anotaciones, debe permitirles determinar correctamente; por consiguiente, se requiere una anotación de `_Success_` .  Observe que `NTSTATUS` y `HRESULT` ya tienen una anotación de `_Success_` compilada en ellas; sin embargo, si especifica posee la anotación de `_Success_` en `NTSTATUS` o `HRESULT`, éste reemplazará la anotación integrada.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; es decir, las anotaciones en `anno_list` se aplican si la función tiene éxito.|  
|`_On_failure_(anno_list)`|Para utilizar sólo cuando `_Success_` también se utilizan para anotar el función\- cualquier explícitamente, o implícitamente con `_Return_type_success_` en un tipo typedef.  Cuando la anotación de `_On_failure_` está presente en un parámetro o valor devuelto de la función, cada anotaciones en `anno_list` \(anno\) se comporta como si estuviera codificado como `_When_(!expr, anno)`, donde el parámetro `expr` a la anotación necesaria de `_Success_` .  Esto significa que la aplicación implícitamente de `_Success_` a todas las POST\- condiciones no solicita `_On_failure_`.|  
|`_Return_type_success_(expr)`|Se puede aplicar a un tipo typedef.  Indica que todas las funciones que devuelven ese tipo y no tienen `_Success_` están escritas como si tuvieran `_Success_(expr)`.  `_Return_type_success_` no se puede utilizar en una función o una definición de puntero a función.|  
|`_Success_(expr)`|`expr` es una expresión que produce un valor r.  Cuando la anotación de `_Success_` está presente en una declaración o definición de función, cada anotación \(`anno`\) de la función y en POST\- condición se comporta como si fuera codificada como `_When_(expr, anno)`.  La anotación de `_Success_` sólo se puede utilizar en una función, no en sus parámetros o tipo de valor devuelto.  Puede haber al menos una anotación de `_Success_` en una función, y no puede estar en ningún `_When_`, `_At_`, o `_Group_`.  Para obtener más información, vea [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)