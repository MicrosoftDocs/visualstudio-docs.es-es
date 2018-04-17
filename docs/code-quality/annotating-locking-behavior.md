---
title: Anotar comportamiento de bloqueo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e42762c77b1ee5fe006a48c4cf7abebea196a0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="annotating-locking-behavior"></a>Anotar comportamiento de bloqueo
Para evitar errores de simultaneidad en el programa multiproceso, siempre que siga una disciplina de bloqueo apropiada y utilizar anotaciones SAL.  
  
 Los errores de simultaneidad son considerablemente difíciles de reproducir, diagnosticar y depurar, puesto que son no deterministas. Razonar sobre la intercalación de subprocesos resulta más difícil y se convierte en muy poco práctico cuando se diseña un cuerpo de código que tiene más de unos pocos subprocesos. Por lo tanto, es recomendable seguir una bloqueo disciplina en los programas multiproceso. Por ejemplo, seguir un orden de bloqueo al adquirir varios bloqueos contribuye a evitar los interbloqueos y adquirir el bloqueo de protección adecuado antes de obtener acceso a un recurso compartido le ayuda a evitar condiciones de carrera.  
  
 Por desgracia, aparentemente simples bloqueos reglas pueden resultar sorprendentemente difíciles de seguir en la práctica. Una limitación fundamental en los lenguajes de programación y los compiladores de hoy en día es que no admiten directamente la especificación y el análisis de los requisitos de simultaneidad. Los programadores deben confiar en los comentarios de código informal express sus intenciones acerca de cómo utilizan bloqueos.  
  
 Anotaciones de SAL de simultaneidad están diseñadas para ayudarle a especificar bloqueos efectos secundarios, bloqueo de responsabilidad, tutela de datos, jerarquía de orden de bloqueos y otros comportamientos de bloqueo esperado. Mediante la realización de reglas implícitas explícita, las anotaciones de SAL simultaneidad proporcionan una manera coherente para documentar cómo el código usa las reglas de bloqueos. Anotaciones de simultaneidad también mejoran la capacidad de herramientas de análisis de código para buscar condiciones de carrera, interbloqueos, las operaciones de sincronización no coincidentes y otros errores de simultaneidad sutiles.  
  
## <a name="general-guidelines"></a>Instrucciones generales  
 Mediante el uso de anotaciones, se debe indicar los contratos que están implícitas mediante las definiciones de función entre implementaciones (destinatarios) y los clientes (llamadores) y express invariables y otras propiedades del programa que puede mejoran el análisis.  
  
 SAL admite muchos tipos diferentes de primitivas de bloqueo, por ejemplo, secciones críticas, exclusiones mutuas, bloqueos por subproceso y otros objetos de recursos. Muchas de las anotaciones de simultaneidad toman una expresión de bloqueo como parámetro. Por convención, se indica un bloqueo mediante la expresión de ruta de acceso del objeto de bloqueo subyacente.  
  
 Algunas reglas de la propiedad de subproceso debe tener en cuenta:  
  
-   Bloqueos por subproceso son bloqueos uncounted que tienen al subproceso desactive la propiedad.  
  
-   Secciones críticas y exclusiones mutuas se cuentan los bloqueos que tengan la propiedad subproceso clara.  
  
-   Los semáforos y eventos se cuentan los bloqueos que no tienen subproceso claro que la propiedad.  
  
## <a name="locking-annotations"></a>Anotaciones de bloqueos  
 En la tabla siguiente se enumera las anotaciones de bloqueos.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueo exclusivo del objeto de bloqueo que se denomina por `expr`.|  
|`_Acquires_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueos del objeto de bloqueo que se denomina por `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|El bloqueo que se denomina por `expr` se adquiere.  Se notifica un error si ya se mantiene el bloqueo.|  
|`_Acquires_shared_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueos compartidos del objeto de bloqueo que se denomina por `expr`.|  
|`_Create_lock_level_(name)`|Una instrucción que declara el símbolo `name` como un nivel de bloqueo para que se pueden utilizar en las anotaciones `_Has_Lock_level_` y `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Anota cualquier objeto para refinar la información de tipo de un objeto de recurso. A veces se utiliza un tipo común para los diferentes tipos de recursos y el tipo sobrecargado no es suficiente para distinguir los requisitos semántica entre los distintos recursos. Esta es una lista de predefinidos `kind` parámetros:<br /><br /> `_Lock_kind_mutex_`<br /> Identificador de tipo de bloqueo exclusiones mutuas.<br /><br /> `_Lock_kind_event_`<br /> Id. de clase de eventos de bloqueo.<br /><br /> `_Lock_kind_semaphore_`<br /> Identificador de tipo de bloqueo para semáforos.<br /><br /> `_Lock_kind_spin_lock_`<br /> Identificador de tipo de bloqueo para bloqueos por subproceso.<br /><br /> `_Lock_kind_critical_section_`<br /> Id. de tipo de secciones críticas de bloqueo.|  
|`_Has_lock_level_(name)`|Anota un objeto de bloqueo y le asigna el nivel de bloqueo de `name`.|  
|`_Lock_level_order_(name1, name2)`|Una instrucción que proporciona el bloqueo de ordenación entre `name1` y `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Anota una función e indica que en post especifican los dos bloqueos, `expr1` y `expr2`, se tratan como si fueran el mismo objeto de bloqueo.|  
|`_Releases_exclusive_lock_(expr)`|Anota una función e indica que en post indican el disminuye de función en uno el recuento de bloqueo exclusivo del objeto de bloqueo que se denomina por `expr`.|  
|`_Releases_lock_(expr)`|Anota una función e indica que en post indican el disminuye de función en uno el recuento de bloqueos del objeto de bloqueo que se denomina por `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|El bloqueo que se denomina por `expr` se libera. Se notifica un error si no se mantiene actualmente el bloqueo.|  
|`_Releases_shared_lock_(expr)`|Anota una función e indica que en post indican el disminuye de función en uno el recuento de bloqueos compartidos del objeto de bloqueo que se denomina por `expr`.|  
|`_Requires_lock_held_(expr)`|Anota una función e indica que en anteriores indican el recuento de bloqueos del objeto que se denomina por `expr` es al menos uno.|  
|`_Requires_lock_not_held_(expr)`|Anota una función e indica que en anteriores indican el recuento de bloqueos del objeto que se denomina por `expr` es cero.|  
|`_Requires_no_locks_held_`|Anota una función e indica que los recuentos de bloqueo de todos los bloqueos que se sabe que el Comprobador de cero.|  
|`_Requires_shared_lock_held_(expr)`|Anota una función e indica que en anteriores indican el recuento de bloqueos compartidos del objeto que se denomina por `expr` es al menos uno.|  
|`_Requires_exclusive_lock_held_(expr)`|Anota una función e indica que en anteriores indican el número de un bloqueo exclusivo del objeto que recibió el nombre `expr` es al menos uno.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Intrínsecos de SAL para objetos de bloqueo no expuestos  
 Algunos objetos de bloqueo no se exponen mediante la implementación de las funciones de bloqueos asociadas.  En la tabla siguiente se enumera las variables intrínsecas de SAL que habilitan las anotaciones en funciones que operan en los objetos de bloqueo no expuestos.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Describe el bloqueo de giro de cancelación.|  
|`_Global_critical_region_`|Describe la región crítica.|  
|`_Global_interlock_`|Describe las operaciones de interbloqueos.|  
|`_Global_priority_region_`|Describe la región de prioridad.|  
  
## <a name="shared-data-access-annotations"></a>Anotaciones de acceso de datos compartido  
 En la tabla siguiente se enumera las anotaciones para el acceso a datos compartidos.  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Anota una variable e indica que cada vez que se tiene acceso a la variable, el recuento de bloqueos del objeto de bloqueo que se denomina por `expr` es al menos uno.|  
|`_Interlocked_`|Anota una variable y es equivalente a `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|El parámetro de función anotado es el operando de destino de una de las distintas funciones de Interlocked.  Los operandos deben tener propiedades adicionales específicas.|  
|`_Write_guarded_by_(expr)`|Anota una variable e indica que cada vez que la variable se ha modificado, el recuento de bloqueos del objeto de bloqueo que se denomina por `expr` es al menos uno.|  
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)   
 [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)