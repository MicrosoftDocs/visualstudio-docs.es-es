---
title: Conjunto de reglas Reglas mínimas nativas
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5646986381907d6ba524b27ae28985e579d6e379
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600030"
---
# <a name="native-minimum-rules-rule-set"></a>Conjunto de reglas Reglas mínimas nativas

Las reglas mínimas nativas de Microsoft se centran en los problemas más críticos del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación.

Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para los proyectos nativos.

|Regla|Descripción|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uso de la memoria sin inicializar|
|[C6011](/cpp/code-quality/c6011)|Desreferenciación de un puntero null|
|[C6029](/cpp/code-quality/c6029)|Uso de un valor sin comprobar|
|[C6053](/cpp/code-quality/c6053)|Terminación en cero de la llamada|
|[C6059](/cpp/code-quality/c6059)|Concatenación incorrecta|
|[C6063](/cpp/code-quality/c6063)|Falta el argumento de cadena para la función de formato|
|[C6064](/cpp/code-quality/c6064)|Falta el argumento de entero para la función de formato|
|[C6066](/cpp/code-quality/c6066)|Falta el argumento de puntero para la función de formato|
|[C6067](/cpp/code-quality/c6067)|Falta el argumento de puntero de cadena para la función de formato|
|[C6101](/cpp/code-quality/c6101)|Devolución de memoria sin inicializar|
|[C6200](/cpp/code-quality/c6200)|El índice supera el valor máximo para el búfer|
|[C6201](/cpp/code-quality/c6201)|El índice supera el valor máximo para el búfer de pila|
|[C6270](/cpp/code-quality/c6270)|Falta el argumento float para la función de formato|
|[C6271](/cpp/code-quality/c6271)|Argumento adicional para la función de formato|
|[C6272](/cpp/code-quality/c6272)|Argumento no flotante para la función de formato|
|[C6273](/cpp/code-quality/c6273)|Argumento no entero para la función de formato|
|[C6274](/cpp/code-quality/c6274)|Argumento sin caracteres para la función de formato|
|[C6276](/cpp/code-quality/c6276)|Conversión de cadena no válida|
|[C6277](/cpp/code-quality/c6277)|Llamada no válida a CreateProcess|
|[C6284](/cpp/code-quality/c6284)|Argumento de objeto no válido para la función de formato|
|[C6290](/cpp/code-quality/c6290)|Prioridad entre operadores NOT lógico y AND bit a bit|
|[C6291](/cpp/code-quality/c6291)|Prioridad entre operadores NOT lógico y OR bit a bit|
|[C6302](/cpp/code-quality/c6302)|Argumento de cadena de caracteres no válido para la función de formato|
|[C6303](/cpp/code-quality/c6303)|Argumento de cadena de caracteres anchos no válido para la función de formato|
|[C6305](/cpp/code-quality/c6305)|Error de coincidencia en el uso de size y count|
|[C6306](/cpp/code-quality/c6306)|Llamada incorrecta a función de argumento variable|
|[C6328](/cpp/code-quality/c6328)|Error de coincidencia de tipo de argumento potencial|
|[C6385](/cpp/code-quality/c6385)|Saturación de lectura|
|[C6386](/cpp/code-quality/c6386)|Saturación de escritura|
|[C6387](/cpp/code-quality/c6387)|Valor de parámetro no válido|
|[C6500](/cpp/code-quality/c6500)|Propiedad de atributo no válida|
|[C6501](/cpp/code-quality/c6501)|Valores de propiedad de atributo en conflicto|
|[C6503](/cpp/code-quality/c6503)|Las referencias no pueden ser null|
|[C6504](/cpp/code-quality/c6504)|Null en valores que no son de puntero|
|[C6505](/cpp/code-quality/c6505)|MustCheck en valores void|
|[C6506](/cpp/code-quality/c6506)|Tamaño de búfer en valores que no son de puntero o matriz|
|[C6508](/cpp/code-quality/c6508)|Acceso de escritura en valores constantes|
|[C6509](/cpp/code-quality/c6509)|Return usado en condición previa|
|[C6510](/cpp/code-quality/c6510)|NullTerminated en valores que no son de puntero|
|[C6511](/cpp/code-quality/c6511)|MustCheck debe ser Yes o No|
|[C6513](/cpp/code-quality/c6513)|ElementSize sin tamaño de búfer|
|[C6514](/cpp/code-quality/c6514)|El tamaño del búfer supera el tamaño de la matriz|
|[C6515](/cpp/code-quality/c6515)|Tamaño de búfer en valores que no son de puntero|
|[C6516](/cpp/code-quality/c6516)|No hay propiedades del atributo|
|[C6517](/cpp/code-quality/c6517)|Tamaño válido en búfer no legible|
|[C6518](/cpp/code-quality/c6518)|Tamaño de escritura en búfer no modificable|
|[C6522](/cpp/code-quality/c6522)|Tipo de cadena de tamaño no válido|
|[C6525](/cpp/code-quality/c6525)|Cadena de tamaño no válida, ubicación inaccesible|
|[C6527](/cpp/code-quality/c6527)|Anotación no válida: la propiedad 'NeedsRelease' no se puede usar en valores de tipo void|
|[C6530](/cpp/code-quality/c6530)|Estilo de cadena de formato no reconocido|
|[C6540](/cpp/code-quality/c6540)|El uso de anotaciones de atributo en esta función invalidará todas las anotaciones __declspec existentes|
|[C6551](/cpp/code-quality/c6551)|Especificación de tamaño no válido: no se puede analizar la expresión|
|[C6552](/cpp/code-quality/c6552)|Valor Deref= o Notref= no válido: no se puede analizar la expresión|
|[C6701](/cpp/code-quality/c6701)|Este no es un valor Yes/No/Maybe válido|
|[C6702](/cpp/code-quality/c6702)|Este no es un valor de cadena|
|[C6703](/cpp/code-quality/c6703)|El valor no es un número|
|[C6704](/cpp/code-quality/c6704)|Error de expresión de anotación inesperado|
|[C6705](/cpp/code-quality/c6705)|El número esperado de argumentos para la anotación no coincide con el número real de argumentos para la anotación|
|[C6706](/cpp/code-quality/c6706)|Error inesperado de la anotación|
|[C26450](/cpp/code-quality/C26450)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](/cpp/code-quality/C26451)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](/cpp/code-quality/C26452)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](/cpp/code-quality/C26453)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](/cpp/code-quality/C26454)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](/cpp/code-quality/C26495)|MEMBER_UNINIT|
|[C28021](/cpp/code-quality/c28021)|El parámetro que se va a anotar debe ser un puntero|
|[C28182](/cpp/code-quality/c28182)|Desreferenciación de un puntero null. El puntero contiene el mismo valor NULL que otro puntero.|
|[C28202](/cpp/code-quality/c28202)|Referencia no válida a un miembro no estático|
|[C28203](/cpp/code-quality/c28203)|Referencia ambigua a un miembro de la clase.|
|[C28205](/cpp/code-quality/c28205)|\_Correcto \_ o \_ en \_ caso de error \_ usado en un contexto no válido|
|[C28206](/cpp/code-quality/c28206)|El operando izquierdo señala a un struct, use '->'|
|[C28207](/cpp/code-quality/c28207)|El operando izquierdo es un struct, use '->'|
|[C28220](/cpp/code-quality/c28210)|Las anotaciones del contexto __on_failure no deben estar en un contexto previo explícito|
|[C28211](/cpp/code-quality/c28211)|Se esperaba un nombre de contexto estático para SAL_context|
|[C28212](/cpp/code-quality/c28212)|Se esperaba una expresión de puntero para la anotación|
|[C28213](/cpp/code-quality/c28213)|La \_ anotación usar anotaciones \_ decl \_ \_ debe usarse para hacer referencia, sin modificación, a una declaración anterior.|
|[C28214](/cpp/code-quality/c28214)|Los nombres de los parámetros de atributo deben ser p1...p9|
|[C28215](/cpp/code-quality/c28215)|typefix no se puede aplicar a un parámetro que ya tenga un typefix|
|[C28216](/cpp/code-quality/c28216)|La anotación checkReturn solamente se aplica a las condiciones posteriores del parámetro de la función específica.|
|[C28217](/cpp/code-quality/c28217)|Para la función, el número de parámetros de la anotación no coincide con el encontrado en el archivo|
|[C28218](/cpp/code-quality/c28218)|En el caso del parámetro de función, el parámetro de la anotación no coincide con el que se encuentra en el archivo.|
|[C28219](/cpp/code-quality/c28219)|Se esperaba un miembro de enumeración para el parámetro de la anotación|
|[C28220](/cpp/code-quality/c28220)|Se esperaba una expresión de entero para el parámetro de la anotación|
|[C28221](/cpp/code-quality/c28221)|Se esperaba una expresión de cadena para el parámetro de la anotación|
|[C28222](/cpp/code-quality/c28222)|Se esperaba __yes, \__no, o \__maybe para la anotación|
|[C28223](/cpp/code-quality/c28223)|No se encontró el token o identificador para la anotación, parámetro|
|[C28224](/cpp/code-quality/c28224)|La anotación requiere parámetros|
|[C28225](/cpp/code-quality/c28225)|No se encontró el número correcto de parámetros necesarios en la anotación|
|[C28226](/cpp/code-quality/c28226)|La anotación no puede ser un PrimOp (en la declaración actual)|
|[C28227](/cpp/code-quality/c28227)|La anotación no puede ser un PrimOp (consulte la declaración anterior)|
|[C28228](/cpp/code-quality/c28228)|Parámetro de anotación: no se puede usar un tipo en las anotaciones|
|[C28229](/cpp/code-quality/c28229)|La anotación no admite parámetros|
|[C28230](/cpp/code-quality/c28230)|El tipo de parámetro no tiene ningún miembro.|
|[C28231](/cpp/code-quality/c28231)|La anotación solo es válida en la matriz|
|[C28232](/cpp/code-quality/c28232)|pre, post o deref no se aplican a ninguna anotación|
|[C28233](/cpp/code-quality/c28233)|pre, post o deref se aplican a un bloque|
|[C28234](/cpp/code-quality/c28234)|La expresión __at no se aplica a la función actual|
|[C28235](/cpp/code-quality/c28235)|La función no puede actuar por sí sola como una anotación|
|[C28236](/cpp/code-quality/c28236)|La anotación no se puede usar en una expresión|
|[C28237](/cpp/code-quality/c28237)|La anotación del parámetro ya no se admite|
|[C28238](/cpp/code-quality/c28238)|La anotación del parámetro tiene más de un valor, stringValue y longValue Use paramn=xxx|
|[C28239](/cpp/code-quality/c28239)|La anotación del parámetro tiene el valor stringValue o longValue, y paramn=xxx. Use solo paramn=xxx|
|[C28240](/cpp/code-quality/c28240)|La anotación del parámetro tiene param2 pero no param1|
|[C28241](/cpp/code-quality/c28241)|La anotación para la función del parámetro no se reconoce|
|[C28243](/cpp/code-quality/c28243)|La anotación para la función del parámetro requiere más desreferenciaciones de las que permite el tipo real anotado|
|[C28245](/cpp/code-quality/c28245)|La anotación para la función anota 'this' en una en una función no miembro|
|[C28246](/cpp/code-quality/c28246)|La anotación del parámetro para la función no coincide con el tipo del parámetro|
|[C28250](/cpp/code-quality/c28250)|Anotación incoherente de la función: la instancia anterior tiene un error.|
|[C28251](/cpp/code-quality/c28251)|Anotación incoherente de la función: esta instancia tiene un error.|
|[C28252](/cpp/code-quality/c28252)|Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.|
|[C28253](/cpp/code-quality/c28253)|Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() no se admite en anotaciones|
|[C28262](/cpp/code-quality/c28262)|Se encontró un error de sintaxis de anotación en la función, para la anotación|
|[C28263](/cpp/code-quality/c28263)|Se encontró un error de sintaxis en una anotación condicional para la anotación intrínseca|
|[C28267](/cpp/code-quality/c28267)|Se encontró un error de sintaxis de anotaciones en la función.|
|[C28272](/cpp/code-quality/c28272)|La anotación del parámetro de la función, al examinar su incoherencia con la declaración de la función|
|[C28273](/cpp/code-quality/c28273)|Para la función, las pistas son incoherentes con la declaración de la función|
|[C28275](/cpp/code-quality/c28275)|El parámetro para el valor de la \_ macro \_ \_ es null|
|[C28279](/cpp/code-quality/c28279)|Para el símbolo, se encontró un 'begin' sin un 'end' coincidente|
|[C28280](/cpp/code-quality/c28280)|Para el símbolo, se encontró un 'end' sin un 'begin' coincidente|
|[C28282](/cpp/code-quality/c28282)|Las cadenas de formato deben estar en las condiciones previas|
|[C28285](/cpp/code-quality/c28285)|Para la función, error de sintaxis en el parámetro|
|[C28286](/cpp/code-quality/c28286)|Para la función, error de sintaxis cerca del final|
|[C28287](/cpp/code-quality/c28287)|Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no reconocido)|
|[C28288](/cpp/code-quality/c28288)|Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no válido)|
|[C28289](/cpp/code-quality/c28289)|Para la función: ReadableTo o WritableTo no tenían una especificación de límite como parámetro|
|[C28290](/cpp/code-quality/c28290)|la anotación de la función contiene más valores External que el número real de parámetros|
|[C28291](/cpp/code-quality/c28291)|El valor null/notnull posterior en el nivel 0 de desreferenciación carece de sentido para la función.|
|[C28300](/cpp/code-quality/c28300)|Operandos de expresión de tipos no compatibles para el operador|
|[C28301](/cpp/code-quality/c28301)|No hay anotaciones para la primera declaración de la función.|
|[C28302](/cpp/code-quality/c28302)|Se encontró un operador \_Deref\_ adicional en la anotación.|
|[C28303](/cpp/code-quality/c28303)|Se encontró un operador \_Deref\_ ambiguo en la anotación.|
|[C28304](/cpp/code-quality/c28304)|Se encontró un operador \_Notref\_ mal colocado aplicado al token.|
|[C28305](/cpp/code-quality/c28305)|Se descubrió un error al analizar un token.|
|[C28350](/cpp/code-quality/c28350)|La anotación describe una situación no aplicable de forma condicional.|
|[C28351](/cpp/code-quality/c28351)|La anotación describe dónde no se puede usar un valor dinámico (una variable) en la condición.|