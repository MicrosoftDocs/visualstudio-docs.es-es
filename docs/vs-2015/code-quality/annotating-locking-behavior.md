---
title: Anotar comportamiento de bloqueo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f09b38ceb4a6824ec38f0d9206cf37e0f056ce28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790765"
---
# <a name="annotating-locking-behavior"></a>Anotar comportamiento de bloqueo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de c/c ++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Introducción a SAL](../code-quality/understanding-sal.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar comportamiento de la función](../code-quality/annotating-function-behavior.md)   
 [Anotar las clases y estructuras](../code-quality/annotating-structs-and-classes.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funciones intrínsecas](../code-quality/intrinsic-functions.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)   
 [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)



