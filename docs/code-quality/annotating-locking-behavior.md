---
title: Anotar comportamiento de bloqueo
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4ee8e68cea1a4f6b708b304b6ca889d29eff0bad
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690326"
---
# <a name="annotating-locking-behavior"></a>Anotar comportamiento de bloqueo
Para evitar errores de simultaneidad en el programa multiproceso, siempre que siga una disciplina de bloqueo apropiada y utilizar anotaciones SAL.

 Los errores de simultaneidad son considerablemente difíciles de reproducir, diagnosticar y depurar porque son no deterministas. Resulta más difícil razonar sobre la intercalación de subprocesos y pasa a ser práctico cuando se diseña un cuerpo de código que tiene más de unos pocos subprocesos. Por lo tanto, es recomendable a seguir una disciplina de bloqueo en los programas multiproceso. Por ejemplo, seguir un orden de bloqueo mientras adquirir varios bloqueos ayuda a evitar los interbloqueos y adquirir el bloqueo de protección adecuado antes de acceder a un recurso compartido le ayuda a evitar las condiciones de carrera.

 Por desgracia, aparentemente simples reglas de bloqueos pueden ser sorprendentemente difíciles de seguir en la práctica. Una limitación fundamental en compiladores y lenguajes de programación de hoy en día es que no admite directamente la especificación y el análisis de los requisitos de simultaneidad. Los programadores tienen que depender de comentarios del código informal para expresar sus intenciones acerca de cómo usan bloqueos.

 Anotaciones de SAL de simultaneidad están diseñadas para ayudarle a especificar bloqueos efectos secundarios, el bloqueo de responsabilidad, tutela de datos, jerarquía de orden de bloqueo y otros comportamientos de bloqueo esperado. Mediante la realización de las reglas implícitas explícitas, las anotaciones de SAL simultaneidad proporcionan una manera coherente para documentar cómo el código usa las reglas de bloqueos. Las anotaciones de simultaneidad también mejoran la capacidad de herramientas de análisis de código para encontrar las condiciones de carrera, interbloqueos, las operaciones de sincronización no coincidentes y otros errores sutiles de simultaneidad.

## <a name="general-guidelines"></a>Instrucciones generales
 Mediante el uso de anotaciones, puede indicar los contratos que están implícitos en las definiciones de función entre implementaciones (destinatarios) y los clientes (llamadores) y las invariantes express y otras propiedades del programa que puede mejoran el análisis.

 SAL admite muchos tipos diferentes de primitivas de bloqueo, por ejemplo, secciones críticas, exclusiones mutuas, bloqueos de giro y otros objetos de recursos. Muchas de las anotaciones de simultaneidad toman una expresión de bloqueo como un parámetro. Por convención, se indica un bloqueo mediante la expresión de ruta de acceso del objeto subyacente de bloqueo.

 Algunas reglas de la propiedad de subprocesos debe tener en cuenta:

-   Bloqueos de giro son bloqueos uncounted que tienen la propiedad de subprocesos no cifrado.

-   Secciones críticas y las exclusiones mutuas se cuentan los bloqueos que tienen la propiedad clara de subproceso.

-   Los semáforos y eventos se cuentan los bloqueos que no tienen la propiedad de subprocesos no cifrado.

## <a name="locking-annotations"></a>Anotaciones de bloqueos
 En la tabla siguiente se enumera las anotaciones de bloqueos.

|Anotación|Descripción|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueo exclusivo del objeto de bloqueo que se denomina por `expr`.|
|`_Acquires_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueos del objeto de bloqueo que se denomina por `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|El bloqueo que se denomina por `expr` se adquiere.  Se notifica un error si ya se mantiene el bloqueo.|
|`_Acquires_shared_lock_(expr)`|Anota una función e indica que en la entrada de estado de la función aumenta en uno el recuento de bloqueos compartidos del objeto de bloqueo que se denomina por `expr`.|
|`_Create_lock_level_(name)`|Una instrucción que declara el símbolo `name` sea un nivel de bloqueo para que se pueden usar en las anotaciones `_Has_Lock_level_` y `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Anota cualquier objeto para restringir la información de tipo de un objeto de recurso. A veces se usa un tipo común para los diferentes tipos de recursos y el tipo sobrecargado no es suficiente para distinguir entre varios recursos de los requisitos de semánticos. Esta es una lista de predefinidos `kind` parámetros:<br /><br /> `_Lock_kind_mutex_`<br /> Tipo Id. de bloqueo para las exclusiones mutuas.<br /><br /> `_Lock_kind_event_`<br /> Identificador de tipo para los eventos de bloqueo.<br /><br /> `_Lock_kind_semaphore_`<br /> Id. de tipo para los semáforos de bloqueo.<br /><br /> `_Lock_kind_spin_lock_`<br /> Tipo Id. de bloqueo para bloqueos de giro.<br /><br /> `_Lock_kind_critical_section_`<br /> Tipo Id. de bloqueo para las secciones críticas.|
|`_Has_lock_level_(name)`|Anota un objeto de bloqueo y le asigna el nivel de bloqueo de `name`.|
|`_Lock_level_order_(name1, name2)`|Una instrucción que proporciona el bloqueo de ordenación entre `name1` y `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Anota una función y se indica en la entrada de estado los dos bloqueos, `expr1` y `expr2`, se tratan como si fueran el mismo objeto de bloqueo.|
|`_Releases_exclusive_lock_(expr)`|Anota una función e indica que en post estado disminuye de la función en uno el recuento de bloqueo exclusivo del objeto de bloqueo que se denomina por `expr`.|
|`_Releases_lock_(expr)`|Anota una función e indica que en post estado disminuye de la función en uno el recuento de bloqueos del objeto de bloqueo que se denomina por `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|El bloqueo que se denomina por `expr` se libera. Se notifica un error si no se mantiene actualmente el bloqueo.|
|`_Releases_shared_lock_(expr)`|Anota una función e indica que en post estado disminuye de la función en uno el recuento de bloqueos compartidos del objeto de bloqueo que se denomina por `expr`.|
|`_Requires_lock_held_(expr)`|Anota una función e indica que en pre estado, el recuento de bloqueos del objeto que recibe el nombre de `expr` como mínimo.|
|`_Requires_lock_not_held_(expr)`|Anota una función e indica que en pre estado, el recuento de bloqueos del objeto que recibe el nombre de `expr` es cero.|
|`_Requires_no_locks_held_`|Anota una función e indica que los recuentos de bloqueo de todos los bloqueos que se sabe que el Comprobador de cero.|
|`_Requires_shared_lock_held_(expr)`|Anota una función e indica que en pre estado, el recuento de bloqueos compartidos del objeto que recibe el nombre de `expr` como mínimo.|
|`_Requires_exclusive_lock_held_(expr)`|Anota una función e indica que en pre estado, el recuento de bloqueo exclusivo del objeto que recibe el nombre de `expr` como mínimo.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Intrínsecos de SAL para objetos de bloqueo no expuestos
 Ciertos objetos de bloqueo no se exponen mediante la implementación de las funciones de bloqueos asociadas.  En la tabla siguiente se enumera las variables intrínsecas de SAL que habilitan las anotaciones en las funciones que operan en los objetos de bloqueo no expuestos.

|Anotación|Descripción|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Describe el bloqueo de giro de cancelación.|
|`_Global_critical_region_`|Describe la región crítica.|
|`_Global_interlock_`|Describe las operaciones de interbloqueos.|
|`_Global_priority_region_`|Describe la región de prioridad.|

## <a name="shared-data-access-annotations"></a>Anotaciones de acceso de datos compartidos
 En la tabla siguiente se enumera las anotaciones para el acceso a datos compartidos.

|Anotación|Descripción|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Anota una variable e indica que cada vez que se accede a la variable, el recuento de bloqueos del objeto de bloqueo que se denomina por `expr` como mínimo.|
|`_Interlocked_`|Anota una variable y es equivalente a `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|El parámetro de función anotado es el operando de destino de una de las distintas funciones Interlocked.  Los operandos deben tener propiedades adicionales específicas.|
|`_Write_guarded_by_(expr)`|Anota una variable e indica que cada vez que la variable se modifica, el recuento de bloqueos del objeto de bloqueo que se denomina por `expr` como mínimo.|


## <a name="smart-lock-and-raii-annotations"></a>Smart Lock y RAII anotaciones
 Cerraduras inteligentes suelen incluir bloqueos nativos y administran su duración. La siguiente tabla enumera las anotaciones que pueden utilizarse con cerraduras inteligentes y RAII patrones con compatibilidad para de codificación `move` semántica.

|Anotación|Descripción|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Indica que el analizador de suponer que se ha adquirido un bloqueo inteligente. Esta anotación espera un tipo de bloqueo de referencia como su parámetro.|
|`_Analysis_assume_smart_lock_released_`|Indica que el analizador de suponer que se ha liberado un bloqueo inteligente. Esta anotación espera un tipo de bloqueo de referencia como su parámetro.|
|`_Moves_lock_(target, source)`|Describe `move constructor` operación que transfiere el estado de bloqueo de la `source` de objeto para el `target`. El `target` se considera un objeto recién creado, por lo que cualquier estado que tenía antes de que se pierde y reemplazado por el `source` estado. El `source` es también restablecer a un estado limpio con ningún destino de recuentos o alias de bloqueo, pero los alias que apunte a él no se modificarán.|
|`_Replaces_lock_(target, source)`|Describe `move assignment operator` semántica donde se libera el bloqueo de destino antes de transferir el estado desde el origen. Se puede considerar como una combinación de `_Moves_lock_(target, source)` precedido por un `_Releases_lock_(target)`.|
|`_Swaps_locks_(left, right)`|Describe el estándar `swap` comportamiento que se da por supuesto que los objetos `left` y `right` su estado de exchange. El estado que se intercambian incluye destino recuento y alias de bloqueo, si está presente. Los alias que apuntan a la `left` y `right` objetos permanecen sin cambios.|
|`_Detaches_lock_(detached, lock)`|Describe un escenario en el que un tipo de contenedor de bloqueo permite disociación con sus recursos independientes. Esto es similar a cómo `std::unique_ptr` funciona con su puntero interno: permite a los programadores extraer el puntero y dejar su contenedor de puntero inteligente en un estado limpio. Una lógica similar es compatible con `std::unique_lock` y se pueden implementar en contenedores de bloqueo personalizada. El bloqueo desasociado conserva su estado (bloqueo recuento y alias de destino, si existe), mientras se restablece el contenedor que contiene cero el número de bloqueos y ningún destino de creación de alias, conservando sus propios alias. No hay ninguna operación en los recuentos de bloqueo (adquisición y liberación). Esta anotación se comporta exactamente como `_Moves_lock_` , salvo que el argumento desasociado debe ser `return` lugar `this`.|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
- [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)