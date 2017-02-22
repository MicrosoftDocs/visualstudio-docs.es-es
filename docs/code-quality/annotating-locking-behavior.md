---
title: "Anotar comportamiento de bloqueo | Microsoft Docs"
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
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Anotar comportamiento de bloqueo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para evitar errores de simultaneidad en el programa multiproceso, siga una disciplina adecuada de bloqueo y utilice siempre las anotaciones SAL.  
  
 Errores de simultaneidad son notorio difíciles de reproducir, de diagnosticar, y depurar porque son no deterministas.  El razonar acerca de la intercalación de subprocesos es difícil en el mejor de los casos, y se práctico si está diseñando un cuerpo de código que tiene más que algunos subprocesos.  Por consiguiente, se recomienda realizar una disciplina de bloqueo en programas multiproceso.  Por ejemplo, obedeciendo un bloqueo petición mientras la adquisición de bloqueos ayuda a evitar interbloqueos, y adquiriendo el bloqueo apropiado el guardar antes de ayuda de acceso de un recurso compartido evitar condiciones de carrera.  
  
 Desgraciadamente, las reglas aparentemente simples de bloqueo pueden ser sorprendente difíciles de seguimiento en el laboratorio.  Una limitación fundamental en los lenguajes de programación y en los compiladores actuales es que no permiten especificar y analizar directamente los requisitos de simultaneidad.  Los desarrolladores tienen que confiar en comentarios informales de código para expresar sus intenciones sobre cómo utilizan bloqueos.  
  
 Las anotaciones de simultaneidad SAL están diseñadas para ayudarle a especificar los efectos secundarios de bloqueo, la responsabilidad del bloqueo, la tutela de los datos, la jerarquía del orden de bloqueo, y otro comportamiento esperado del bloqueo.  Crear reglas implícitas explícitas, las anotaciones de simultaneidad SAL proporcionan una manera coherente para implementar un documento cómo el código utiliza reglas de bloqueo.  Las anotaciones de simultaneidad también mejoran la capacidad de herramientas de análisis de código de encontrar condiciones de carrera, interbloqueos, operaciones no coincidentes de la sincronización, y otros errores sutiles de simultaneidad.  
  
## Instrucciones generales  
 Mediante anotaciones, puede establecer los contratos que son definiciones de función implícita en entre las implementaciones \(destinatarios\) y los clientes \(llamadores\), y expresa invariables y otras propiedades de programa que puede mejorar aún más análisis.  
  
 SAL admite muchos tipos distintos de bloqueo primitivo\- para el ejemplo, secciones críticas, exclusiones mutuas, retorno bloqueos, y otros objetos de recursos.  Muchas de las anotaciones de simultaneidad toman una expresión de bloqueo como parámetro.  Por convención, un bloqueo se indica mediante la expresión de la ruta de acceso al objeto subyacente de bloqueo.  
  
 Algunos subprocesos reglas de propiedad para tener en cuenta:  
  
-   La vuelta bloqueos es uncounted bloqueos que tiene la propiedad clara del subproceso.  
  
-   Se cuentan las exclusiones mutuas y las secciones críticas bloqueos que tienen propiedad clara del subproceso.  
  
-   Se cuentan los semáforos y eventos bloqueos que no tienen propiedad clara del subproceso.  
  
## Anotaciones de bloqueo  
 La siguiente tabla enumera las anotaciones de bloqueo.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Observe una función y la indica que en estado post la función incrementa en uno el recuento de bloqueo exclusivo del objeto de bloqueo que llama `expr`.|  
|`_Acquires_lock_(expr)`|Observe una función y la indica que en estado post la función incrementa en uno el recuento de bloqueo del objeto de bloqueo que llama `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Se adquiere el bloqueo que llama `expr` .  Se muestra un error si el bloqueo se mantiene ya.|  
|`_Acquires_shared_lock_(expr)`|Observe una función e indica que en estado post los incrementos de la función en uno el recuento compartido de bloqueo del objeto de bloqueo que llama `expr`.|  
|`_Create_lock_level_(name)`|Una instrucción que declara el símbolo `name` para ser un nivel de bloqueo para que se pueda utilizar en las anotaciones `_Has_Lock_level_` y `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Anota cualquier objeto para refinar la información de tipo de un objeto de recursos.  A veces se utiliza un tipo común para diferentes tipos de recursos y el tipo sobrecargado no es suficiente para distinguir los requisitos semánticos entre varios recursos.  A continuación se muestra una lista de parámetros predefinidos de `kind` :<br /><br /> `_Lock_kind_mutex_`<br /> Identificador de tipo de bloqueo para las exclusiones mutuas.<br /><br /> `_Lock_kind_event_`<br /> Identificador de tipo de bloqueo para los eventos.<br /><br /> `_Lock_kind_semaphore_`<br /> Identificador de tipo de bloqueo para los semáforos.<br /><br /> `_Lock_kind_spin_lock_`<br /> Identificador de tipo de bloqueo para los bloqueos de espera \(spin lock\).<br /><br /> `_Lock_kind_critical_section_`<br /> Identificador de tipo de bloqueo para las secciones críticas.|  
|`_Has_lock_level_(name)`|Anota un objeto de bloqueo y le da el bloqueo de nivel de `name`.|  
|`_Lock_level_order_(name1, name2)`|Una expresión que proporciona el orden de bloqueos entre `name1` y `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Observe una función y la indica que en estado de envío que los dos bloqueos, `expr1` y `expr2`, se trata como si fueran el mismo objeto de bloqueo.|  
|`_Releases_exclusive_lock_(expr)`|Observe una función y la indica que en estado post la función reduce por una el recuento de bloqueo exclusivo del objeto de bloqueo que llama `expr`.|  
|`_Releases_lock_(expr)`|Observe una función y la indica que en estado post la función reduce por una el recuento de bloqueo del objeto de bloqueo que llama `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|El bloqueo se libera que llama `expr` .  Se muestra un error si no se mantiene el bloqueo actualmente.|  
|`_Releases_shared_lock_(expr)`|Observe una función e indica que en estado post las disminuciones de la función en uno el recuento compartido de bloqueo del objeto de bloqueo que llama `expr`.|  
|`_Requires_lock_held_(expr)`|Observe una función y la indica que en pre indica el recuento de bloqueo del objeto que llama `expr` es al menos uno.|  
|`_Requires_lock_not_held_(expr)`|Observe una función y la indica que en pre indica el recuento de bloqueo del objeto que llama `expr` es cero.|  
|`_Requires_no_locks_held_`|Observe una función e indica que los recuentos de bloqueo de todos los bloqueos que se sabe el comprobador son cero.|  
|`_Requires_shared_lock_held_(expr)`|Observe una función y la indica que en pre indica el recuento compartido de bloqueo del objeto que llama `expr` es al menos uno.|  
|`_Requires_exclusive_lock_held_(expr)`|Observe una función y la indica que en pre indica el recuento de bloqueo exclusivo del objeto que llama `expr` es al menos uno.|  
  
## Intrínsecos de SAL para objetos de bloqueo no expuestos  
 La implementación de las funciones de bloqueo asociadas no exponen algunos objetos de bloqueo.  La tabla siguiente se enumeran las variables intrínsecas SAL que permiten anotaciones en funciones que operan con esos objetos no expuestos de bloqueo.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Global_cancel_spin_lock_`|Describe el bloqueo return de cancelación.|  
|`_Global_critical_region_`|Describe la región crítica.|  
|`_Global_interlock_`|Describe entrelazó operaciones.|  
|`_Global_priority_region_`|Describe la región de prioridad.|  
  
## Anotaciones de acceso a datos compartidos  
 La tabla siguiente se enumeran las anotaciones para el acceso a datos compartido.  
  
|Anotación|Descripción|  
|---------------|-----------------|  
|`_Guarded_by_(expr)`|Observe una variable e indica que siempre que la variable se almacenan, el recuento de bloqueo del objeto de bloqueo que llama `expr` es al menos uno.|  
|`_Interlocked_`|Anota una variable y es equivalente a `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|El parámetro de función anotado es el operando de destino de una de las diversas funciones de Interlocked.  Esos operandos deben tener propiedades adicionales específicas.|  
|`_Write_guarded_by_(expr)`|Observe una variable e indica siempre que se modifique la variable, el recuento de bloqueo del objeto de bloqueo que llama `expr` es al menos uno.|  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)   
 [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)