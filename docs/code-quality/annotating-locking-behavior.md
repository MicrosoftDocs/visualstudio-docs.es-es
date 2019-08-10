---
title: Anotar comportamiento de bloqueo
ms.date: 11/04/2016
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
ms.openlocfilehash: 68e57a10b9bd36b07a2d4993626604f2a00558ca
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919575"
---
# <a name="annotating-locking-behavior"></a>Anotar comportamiento de bloqueo
Para evitar errores de simultaneidad en el programa multiproceso, siga siempre una disciplina de bloqueo adecuada y use anotaciones SAL.

Los errores de simultaneidad son muy difíciles de reproducir, diagnosticar y depurar porque no son deterministas. La razón por la que la intercalación de subprocesos es más difícil y no resulta práctico cuando se diseña un cuerpo de código que tiene más de unos pocos subprocesos. Por lo tanto, se recomienda seguir una disciplina de bloqueo en los programas multiproceso. Por ejemplo, la continuación de un orden de bloqueo mientras se adquieren varios bloqueos ayuda a evitar los interbloqueos y la adquisición del bloqueo adecuado antes de obtener acceso a un recurso compartido ayuda a evitar las condiciones de carrera.

Desafortunadamente, las reglas de bloqueo aparentemente simples pueden ser sorprendentemente difíciles de seguir en la práctica. Una limitación fundamental en los lenguajes de programación y los compiladores de hoy en día es que no admiten directamente la especificación y el análisis de los requisitos de simultaneidad. Los programadores deben confiar en los comentarios de código informal para expresar sus intenciones sobre cómo usan los bloqueos.

Las anotaciones de SAL de simultaneidad están diseñadas para ayudarle a especificar efectos secundarios de bloqueo, responsabilidad de bloqueo, tutela de datos, jerarquía de pedidos de bloqueos y otro comportamiento de bloqueo esperado. Al hacer que las reglas implícitas sean explícitas, las anotaciones de simultaneidad de SAL proporcionan una manera coherente de documentar el modo en que el código utiliza las reglas de bloqueo. Las anotaciones de simultaneidad también mejoran la capacidad de las herramientas de análisis de código para buscar condiciones de carrera, interbloqueos, operaciones de sincronización no coincidentes y otros errores de simultaneidad sutiles.

## <a name="general-guidelines"></a>Directrices generales
Mediante el uso de anotaciones, puede indicar los contratos que están implícitos en las definiciones de función entre implementaciones (destinatarios) y clientes (llamadores), y expresar invariantes y otras propiedades del programa que pueden mejorar aún más el análisis.

SAL admite muchos tipos diferentes de primitivas de bloqueo, por ejemplo, secciones críticas, exclusiones mutuas, bloqueos de giro y otros objetos de recursos. Muchas anotaciones de simultaneidad toman una expresión de bloqueo como parámetro. Por Convención, la expresión de ruta de acceso del objeto de bloqueo subyacente denota un bloqueo.

Algunas reglas de propiedad de subprocesos que se deben tener en cuenta:

- Los bloqueos de giro son bloqueos sin contar que tienen una propiedad clara de subproceso.

- Las exclusiones mutuas y las secciones críticas son bloqueos contables que tienen una propiedad Clear Thread.

- Los semáforos y eventos son bloqueos contados que no tienen una propiedad clara de subproceso.

## <a name="locking-annotations"></a>Bloquear anotaciones
En la tabla siguiente se enumeran las anotaciones de bloqueo.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Anota una función e indica que en post State la función incrementa en uno el recuento de bloqueos exclusivos del objeto de bloqueo denominado por `expr`.|
|`_Acquires_lock_(expr)`|Anota una función e indica que en post State la función incrementa en uno el recuento de bloqueos del objeto de bloqueo denominado por `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Se adquiere el bloqueo llamado por `expr` .  Se muestra un error si el bloqueo ya se ha mantenido.|
|`_Acquires_shared_lock_(expr)`|Anota una función e indica que en post State la función incrementa en uno el recuento de bloqueos compartido del objeto de bloqueo denominado por `expr`.|
|`_Create_lock_level_(name)`|Instrucción que declara el símbolo `name` para que sea un nivel de bloqueo, de modo que se pueda utilizar en las `_Has_Lock_level_` anotaciones y `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Anota cualquier objeto para refinar la información de tipo de un objeto de recurso. A veces se utiliza un tipo común para diferentes tipos de recursos y el tipo sobrecargado no es suficiente para distinguir los requisitos semánticos entre varios recursos. Esta es una lista de parámetros predefinidos `kind` :<br /><br /> `_Lock_kind_mutex_`<br /> IDENTIFICADOR de tipo de bloqueo para las exclusiones mutuas.<br /><br /> `_Lock_kind_event_`<br /> IDENTIFICADOR de tipo de bloqueo de los eventos.<br /><br /> `_Lock_kind_semaphore_`<br /> IDENTIFICADOR de tipo de bloqueo para semáforos.<br /><br /> `_Lock_kind_spin_lock_`<br /> IDENTIFICADOR de tipo de bloqueo para bloqueos de giro.<br /><br /> `_Lock_kind_critical_section_`<br /> IDENTIFICADOR de tipo de bloqueo para las secciones críticas.|
|`_Has_lock_level_(name)`|Anota un objeto de bloqueo y le da el nivel de bloqueo `name`de.|
|`_Lock_level_order_(name1, name2)`|Instrucción que proporciona la ordenación de bloqueos `name2`entre `name1` y.|
|`_Post_same_lock_(expr1, expr2)`|Anota una función e indica que en el estado post los dos bloqueos `expr1` , `expr2`y se tratan como si fueran el mismo objeto de bloqueo.|
|`_Releases_exclusive_lock_(expr)`|Anota una función e indica que en post State la función disminuye en uno el recuento de bloqueos exclusivos del objeto de bloqueo denominado por `expr`.|
|`_Releases_lock_(expr)`|Anota una función e indica que en post State la función disminuye en uno el recuento de bloqueos del objeto de bloqueo denominado por `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Se libera el bloqueo llamado por `expr` . Se genera un error si el bloqueo no se mantiene actualmente.|
|`_Releases_shared_lock_(expr)`|Anota una función e indica que en post State la función disminuye en uno el recuento de bloqueos compartido del objeto de bloqueo denominado por `expr`.|
|`_Requires_lock_held_(expr)`|Anota una función e indica que, en el estado anterior, el recuento de bloqueos del objeto `expr` denominado por es al menos uno.|
|`_Requires_lock_not_held_(expr)`|Anota una función e indica que, en el estado anterior, el recuento de bloqueos del objeto `expr` denominado por es cero.|
|`_Requires_no_locks_held_`|Anota una función e indica que los recuentos de bloqueos de todos los bloqueos que conoce el comprobador son cero.|
|`_Requires_shared_lock_held_(expr)`|Anota una función e indica que, en el estado anterior, el recuento de bloqueos compartidos `expr` del objeto denominado por es al menos uno.|
|`_Requires_exclusive_lock_held_(expr)`|Anota una función e indica que, en el estado anterior, el recuento de bloqueos exclusivos del objeto `expr` denominado por es al menos uno.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Intrínsecos de SAL para objetos de bloqueo no expuestos
Ciertos objetos de bloqueo no se exponen mediante la implementación de las funciones de bloqueo asociadas.  En la tabla siguiente se enumeran las variables intrínsecas SAL que habilitan las anotaciones en las funciones que operan en esos objetos de bloqueo no expuestos.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Describe el bloqueo de giro de cancelación.|
|`_Global_critical_region_`|Describe la región crítica.|
|`_Global_interlock_`|Describe las operaciones de interbloqueo.|
|`_Global_priority_region_`|Describe la región de prioridad.|

## <a name="shared-data-access-annotations"></a>Anotaciones de acceso a datos compartidos
En la tabla siguiente se enumeran las anotaciones para el acceso a datos compartidos.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Anota una variable e indica que, cada vez que se tiene acceso a la variable, el recuento de bloqueos del objeto `expr` de bloqueo denominado por es al menos uno.|
|`_Interlocked_`|Anota una variable y es equivalente a `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|El parámetro de función anotado es el operando de destino de una de las diversas funciones entrelazadas.  Esos operandos deben tener propiedades adicionales específicas.|
|`_Write_guarded_by_(expr)`|Anota una variable e indica que, cada vez que se modifica la variable, el recuento de bloqueos del objeto de `expr` bloqueo denominado por es al menos uno.|

## <a name="smart-lock-and-raii-annotations"></a>Anotaciones Smart Lock y RAII
Normalmente, los bloqueos inteligentes encapsulan los bloqueos nativos y administran su duración. En la tabla siguiente se enumeran las anotaciones que se pueden usar con los bloqueos inteligentes y los `move` patrones de codificación de RAII con compatibilidad con la semántica.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Indica al analizador que asuma que se ha adquirido un bloqueo inteligente. Esta anotación espera un tipo de bloqueo de referencia como su parámetro.|
|`_Analysis_assume_smart_lock_released_`|Indica al analizador que asuma que se ha lanzado un bloqueo inteligente. Esta anotación espera un tipo de bloqueo de referencia como su parámetro.|
|`_Moves_lock_(target, source)`|Describe `move constructor` la operación que transfiere el `source` estado de bloqueo del objeto `target`a. Se considera un objeto recién construido, por lo que cualquier Estado que tenía antes se pierde y se reemplaza `source` por el estado. `target` También `source` se restablece a un estado limpio sin recuentos de bloqueos o destinos de alias, pero los alias que apuntan a él permanecen inalterados.|
|`_Replaces_lock_(target, source)`|Describe `move assignment operator` la semántica en la que se libera el bloqueo de destino antes de transferir el estado del origen. Esto puede considerarse como una combinación de `_Moves_lock_(target, source)` precedida de un `_Releases_lock_(target)`.|
|`_Swaps_locks_(left, right)`|Describe el comportamiento `swap` estándar que supone que los `left` objetos `right` y intercambian su estado. El estado intercambiado incluye el recuento de bloqueos y el destino de alias, si está presente. Los alias que apuntan a `left` los `right` objetos y permanecen inalterados.|
|`_Detaches_lock_(detached, lock)`|Describe un escenario en el que un tipo de contenedor de bloqueo permite la desasociación con su recurso contenido. Esto es similar a cómo `std::unique_ptr` funciona con su puntero interno: permite a los programadores extraer el puntero y dejar su contenedor de puntero inteligente en un estado limpio. La lógica similar es compatible `std::unique_lock` con y se puede implementar en contenedores de bloqueo personalizados. El bloqueo separado conserva su estado (recuento de bloqueos y destino de alias, si existe), mientras que el contenedor se restablece para que contenga un recuento de bloqueos cero y ningún destino de alias, mientras se conservan sus propios alias. No hay ninguna operación en los recuentos de bloqueos (liberación y adquisición). Esta anotación se comporta exactamente igual que, `_Moves_lock_` salvo que el argumento separado debe ser `return` en lugar de `this`.|

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