---
title: "Funciones intr&#237;nsecas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una expresión en SAL puede ser expresión de C\/C\+\+. \/C \+\+ siempre que es una expresión que no tiene el efecto\- para el ejemplo, \+\+, \-\-, y las llamadas de función todas tienen efectos secundarios en este contexto.  Sin embargo, SAL proporciona algunos objetos de tipo función y algunos símbolos reservados que se pueden utilizar en expresiones SAL.  Estos se conocen como *funciones intrínsecas*.  
  
## Uso general  
 Las anotaciones instrinsic siguientes de la función proporcionan la utilidad general para SAL.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Curr_`|Un sinónimo para el objeto que se está anotando actualmente.  Cuando la anotación de `_At_` está en uso, `_Curr_` es igual que el primer parámetro a `_At_`.  Si no, es el parámetro o toda la función y el valor devuelto al que la anotación se asocia léxico.|  
|`_Inexpressible_(expr)`|Expresa un escenario donde es demasiado complejo el tamaño de un búfer representar usando una anotación expresión\- para el ejemplo, cuando se calcula la exploración de los datos de entrada establecido y después contando miembros seleccionados.|  
|`_Nullterm_length_(param)`|`param` es el número de elementos del búfer hasta el terminador nulo, pero sin incluirlo.  Puede aplicarse a cualquier búfer de tipo no agregado, de tipo no vacío.|  
|`_Old_(expr)`|Cuando se evalúa en la condición previa, `_Old_` devuelve el valor `expr`de entrada.  Cuando se evalúa en POST\- condición, devuelve el valor `expr` como habría evalúa en la condición previa.|  
|`_Param_(n)`|El parámetro `n`\-ésimo de una función, contando desde 1 a `n`, y `n` es una constante entera literal.  Si el parámetro es nombrado, esta anotación es idéntica a obtener acceso al parámetro por nombre. **Note:**  `n` puede hacer referencia a los parámetros posicionales definidos por puntos suspensivos, o se puede utilizar en los prototipos de función donde los nombres no se utilizan.|  
|`return`|La palabra clave reservada `return` de C\/C\+\+ se puede usar en una expresión SAL para indicar el valor devuelto por una función.  El valor sólo está disponible en estado de envío; es un error de sintaxis para utilizarlo en pre estado.|  
  
## Específico de la cadena  
 Las anotaciones siguientes de la función intrínseca habilitan la manipulación de cadenas.  Los cuatro de estas funciones tienen el mismo resultado: para devolver el número de elementos del tipo que se encuentra antes de un carácter null final.  Las diferencias son clases de datos en los elementos se conocen que.  Observe que si desea especificar la longitud de un búfer terminado en null que no se compone de caracteres, utilice la anotación de `_Nullterm_length_(param)` de la sección anterior.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_String_length_(param)`|`param` es el número de elementos en la cadena hasta el terminador nulo, pero sin incluirlo.  Esta anotación se reserva para los tipos de cadena de carácter.|  
|`strlen(param)`|`param` es el número de elementos en la cadena hasta el terminador nulo, pero sin incluirlo.  Esta anotación se reserva para el uso en matrices de caracteres y es similar a la función [strlen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)en tiempo de ejecución de C.|  
|`wcslen(param)`|`param` es el número de elementos en la cadena hasta un terminador nulo \(pero sin incluirlo\).  Esta anotación se reserva para su uso en las matrices de caracteres anchos y es similar a la función [wcslen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)en tiempo de ejecución de C.|  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)