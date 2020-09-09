---
title: Conjunto de reglas Reglas recomendadas nativas
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fd7ba7b742c2615dc8f161c5ea156b4fd0a7f4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600024"
---
# <a name="native-recommended-rules-rule-set"></a>Conjunto de reglas Reglas recomendadas nativas

Las reglas recomendadas nativas se centran en los problemas más graves y habituales del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Este conjunto de reglas incluye todas las reglas del conjunto de reglas [reglas mínimas nativas](native-minimum-rules-rule-set.md) .

Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para los proyectos nativos.

|Regla|Descripción|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uso de la memoria sin inicializar|
|[C6011](/cpp/code-quality/c6011)|Desreferenciación de un puntero null|
|[C6029](/cpp/code-quality/c6029)|Uso de un valor sin comprobar|
|[C6031](/cpp/code-quality/c6031)|Valor devuelto omitido|
|[C6053](/cpp/code-quality/c6053)|Terminación en cero de la llamada|
|[C6054](/cpp/code-quality/c6054)|Falta terminación cero|
|[C6059](/cpp/code-quality/c6059)|Concatenación incorrecta|
|[C6063](/cpp/code-quality/c6063)|Falta el argumento de cadena para la función de formato|
|[C6064](/cpp/code-quality/c6064)|Falta el argumento de entero para la función de formato|
|[C6066](/cpp/code-quality/c6066)|Falta el argumento de puntero para la función de formato|
|[C6067](/cpp/code-quality/c6067)|Falta el argumento de puntero de cadena para la función de formato|
|[C6101](/cpp/code-quality/c6101)|Devolución de memoria sin inicializar|
|[C6200](/cpp/code-quality/c6200)|El índice supera el valor máximo para el búfer|
|[C6201](/cpp/code-quality/c6201)|El índice supera el valor máximo para el búfer de pila|
|[C6214](/cpp/code-quality/c6214)|VALOR HRESULT de conversión no válido en BOOL|
|[C6215](/cpp/code-quality/c6215)|Conversión no válida de BOOL a HRESULT|
|[C6216](/cpp/code-quality/c6216)|VALOR BOOLEANO de conversión insertada en el compilador no válido|
|[C6217](/cpp/code-quality/c6217)|Prueba HRESULT no válida con NOT|
|[C6220](/cpp/code-quality/c6220)|Comparación de HRESULT no válida con-1|
|[C6226](/cpp/code-quality/c6226)|Asignación de HRESULT no válida a-1|
|[C6230](/cpp/code-quality/c6230)|Uso de HRESULT no válido como booleano|
|[C6235](/cpp/code-quality/c6235)|Constante distinta de cero con OR lógico|
|[C6236](/cpp/code-quality/c6236)|OR lógico con constante distinta de cero|
|[C6237](/cpp/code-quality/c6237)|Cero con efectos lógicos y pierde efectos secundarios|
|[C6242](/cpp/code-quality/c6242)|Desenredo local forzado|
|[C6248](/cpp/code-quality/c6248)|Creando DACL null|
|[C6250](/cpp/code-quality/c6250)|Descriptores de dirección no liberados|
|[C6255](/cpp/code-quality/c6255)|Uso no protegido de alloca|
|[C6258](/cpp/code-quality/c6258)|Usar el subproceso Terminate|
|[C6259](/cpp/code-quality/c6259)|Código muerto en un conmutador de bits o limitado|
|[C6260](/cpp/code-quality/c6260)|Uso de aritmética de bytes|
|[C6262](/cpp/code-quality/c6262)|Uso excesivo de la pila|
|[C6263](/cpp/code-quality/c6263)|Usar alloca in (bucle)|
|[C6268](/cpp/code-quality/c6268)|Faltan paréntesis en la conversión|
|[C6269](/cpp/code-quality/c6269)|Desreferencia de puntero omitida|
|[C6270](/cpp/code-quality/c6270)|Falta el argumento float para la función de formato|
|[C6271](/cpp/code-quality/c6271)|Argumento adicional para la función de formato|
|[C6272](/cpp/code-quality/c6272)|Argumento no flotante para la función de formato|
|[C6273](/cpp/code-quality/c6273)|Argumento no entero para la función de formato|
|[C6274](/cpp/code-quality/c6274)|Argumento sin caracteres para la función de formato|
|[C6276](/cpp/code-quality/c6276)|Conversión de cadena no válida|
|[C6277](/cpp/code-quality/c6277)|Llamada no válida a CreateProcess|
|[C6278](/cpp/code-quality/c6278)|Matriz: nueva no coincidente de eliminación escalar|
|[C6279](/cpp/code-quality/c6279)|Escalar-nueva matriz: eliminación no coincidente|
|[C6280](/cpp/code-quality/c6280)|Asignación de memoria: desasignación no coincidente|
|[C6281](/cpp/code-quality/c6281)|Precedencia de relación bit a bit|
|[C6282](/cpp/code-quality/c6282)|La asignación reemplaza la prueba|
|[C6283](/cpp/code-quality/c6283)|Matriz primitiva: no coincide el nuevo escalar-eliminación|
|[C6284](/cpp/code-quality/c6284)|Argumento de objeto no válido para la función de formato|
|[C6285](/cpp/code-quality/c6285)|Logical-or de constantes|
|[C6286](/cpp/code-quality/c6286)|Efectos secundarios que no son de cero o de pérdida|
|[C6287](/cpp/code-quality/c6287)|Prueba redundante|
|[C6288](/cpp/code-quality/c6288)|La inclusión mutua sobre Logical-and es false|
|[C6289](/cpp/code-quality/c6289)|La exclusión mutua sobre el operador lógico or es true|
|[C6290](/cpp/code-quality/c6290)|Prioridad entre operadores NOT lógico y AND bit a bit|
|[C6291](/cpp/code-quality/c6291)|Prioridad entre operadores NOT lógico y OR bit a bit|
|[C6292](/cpp/code-quality/c6292)|Número máximo de bucles|
|[C6293](/cpp/code-quality/c6293)|El número de bucles es inferior al mínimo|
|[C6294](/cpp/code-quality/c6294)|El cuerpo del bucle nunca se ejecutó|
|[C6295](/cpp/code-quality/c6295)|Bucle infinito|
|[C6296](/cpp/code-quality/c6296)|El bucle solo se ejecuta una vez|
|[C6297](/cpp/code-quality/c6297)|Resultado de la conversión de mayúsculas a un tamaño mayor|
|[C6299](/cpp/code-quality/c6299)|Comparación de bits a booleano|
|[C6302](/cpp/code-quality/c6302)|Argumento de cadena de caracteres no válido para la función de formato|
|[C6303](/cpp/code-quality/c6303)|Argumento de cadena de caracteres anchos no válido para la función de formato|
|[C6305](/cpp/code-quality/c6305)|Error de coincidencia en el uso de size y count|
|[C6306](/cpp/code-quality/c6306)|Llamada incorrecta a función de argumento variable|
|[C6308](/cpp/code-quality/c6308)|Pérdida de realloc|
|[C6310](/cpp/code-quality/c6310)|Constante de filtro de excepción no válida|
|[C6312](/cpp/code-quality/c6312)|Bucle de ejecución de excepción continua|
|[C6314](/cpp/code-quality/c6314)|Precedencia OR bit a bit|
|[C6317](/cpp/code-quality/c6317)|No complementario|
|[C6318](/cpp/code-quality/c6318)|Exception continue Search|
|[C6319](/cpp/code-quality/c6319)|Omitido por coma|
|[C6324](/cpp/code-quality/c6324)|Copia de cadena en lugar de comparación de cadenas|
|[C6328](/cpp/code-quality/c6328)|Error de coincidencia de tipo de argumento potencial|
|[C6331](/cpp/code-quality/c6331)|No hay marcas válidas de VirtualFree|
|[C6332](/cpp/code-quality/c6332)|Parámetro no válido de VirtualFree|
|[C6333](/cpp/code-quality/c6333)|VirtualFree tamaño no válido|
|[C6335](/cpp/code-quality/c6335)|Identificador del proceso de fuga|
|[C6381](/cpp/code-quality/c6381)|Falta la información de apagado|
|[C6383](/cpp/code-quality/c6383)|Elemento-Count recuento de bytes: saturación del búfer de recuento|
|[C6384](/cpp/code-quality/c6384)|División de tamaño de puntero|
|[C6385](/cpp/code-quality/c6385)|Saturación de lectura|
|[C6386](/cpp/code-quality/c6386)|Saturación de escritura|
|[C6387](/cpp/code-quality/c6387)|Valor de parámetro no válido|
|[C6388](/cpp/code-quality/c6388)|Valor de parámetro no válido|
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
|[C6995](/cpp/code-quality/c6995)|No se pudo guardar el archivo de registro XML|
|[C26100](/cpp/code-quality/c26100)|Condición de carrera|
|[C26101](/cpp/code-quality/c26101)|No se puede usar la operación de interbloqueo correctamente|
|[C26110](/cpp/code-quality/c26110)|El autor de la llamada no puede contener el bloqueo|
|[C26111](/cpp/code-quality/c26111)|No se pudo liberar el bloqueo del autor de la llamada|
|[C26112](/cpp/code-quality/c26112)|El autor de la llamada no puede contener ningún bloqueo|
|[C26115](/cpp/code-quality/c26115)|No se pudo liberar el bloqueo|
|[C26116](/cpp/code-quality/c26116)|No se puede adquirir o mantener el bloqueo|
|[C26117](/cpp/code-quality/c26117)|Liberación de bloqueo no retenido|
|[C26140](/cpp/code-quality/c26140)|Error de anotación SAL de simultaneidad|
|[C26441](/cpp/code-quality/C26441)|NO_UNNAMED_GUARDS|
|[C26444](/cpp/code-quality/c26444)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](/cpp/code-quality/C26498)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](/cpp/code-quality/c28020)|La expresión no es true en esta llamada|
|[C28021](/cpp/code-quality/c28021)|El parámetro que se va a anotar debe ser un puntero|
|[C28022](/cpp/code-quality/c28022)|Las clases de función de esta función no coinciden con las clases de función de la definición de tipo que se usa para definirla.|
|[C28023](/cpp/code-quality/c28023)|La función que se va a asignar o pasar debe tener una \_ \_ anotación de clase de función \_ para al menos una de las clases.|
|[C28024](/cpp/code-quality/c28024)|El puntero de función al que se asigna se anota con la clase de función, que no está incluida en la lista de clases de función.|
|[C28039](/cpp/code-quality/c28039)|El tipo de parámetro real debe coincidir exactamente con el tipo|
|[C28112](/cpp/code-quality/c28112)|Siempre se debe tener acceso a una variable a la que se tiene acceso a través de una función de interbloqueo a través de una función de interbloqueo.|
|[C28113](/cpp/code-quality/c28113)|Obtener acceso a una variable local a través de una función de interbloqueo|
|[C28125](/cpp/code-quality/c28125)|Se debe llamar a la función desde un bloque try/except|
|[C28137](/cpp/code-quality/c28137)|En su lugar, el argumento variable debe ser una constante (literal)|
|[C28138](/cpp/code-quality/c28138)|En su lugar, el argumento Constant debe ser variable|
|[C28159](/cpp/code-quality/c28159)|Considere la posibilidad de usar otra función en su lugar.|
|[C28160](/cpp/code-quality/c28160)|Error (anotación)|
|[C28163](/cpp/code-quality/c28163)|Nunca se debe llamar a la función desde dentro de un bloque try/except|
|[C28164](/cpp/code-quality/c28164)|El argumento se pasa a una función que espera un puntero a un objeto (no un puntero a un puntero)|
|[C28182](/cpp/code-quality/c28182)|Desreferenciación de un puntero null. El puntero contiene el mismo valor NULL que otro puntero.|
|[C28183](/cpp/code-quality/c28183)|El argumento puede ser un valor y es una copia del valor encontrado en el puntero|
|[C28193](/cpp/code-quality/c28193)|La variable contiene un valor que se debe examinar.|
|[C28196](/cpp/code-quality/c28196)|No se cumple el requisito. (La expresión no se evalúa como true).|
|[C28202](/cpp/code-quality/c28202)|Referencia no válida a un miembro no estático|
|[C28203](/cpp/code-quality/c28203)|Referencia ambigua a un miembro de la clase.|
|[C28205](/cpp/code-quality/c28205)|\_Correcto \_ o \_ en \_ caso de error \_ usado en un contexto no válido|
|[C28206](/cpp/code-quality/c28206)|El operando izquierdo señala a un struct, use '->'|
|[C28207](/cpp/code-quality/c28207)|El operando izquierdo es un struct, use '->'|
|[C28209](/cpp/code-quality/c28209)|La declaración del símbolo tiene una declaración en conflicto|
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
|[C28244](/cpp/code-quality/c28244)|La anotación de la función tiene un parámetro o anotación externa no analizable|
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
|[C28306](/cpp/code-quality/c28306)|La anotación en el parámetro es obsoleta|
|[C28307](/cpp/code-quality/c28307)|La anotación en el parámetro es obsoleta|
|[C28350](/cpp/code-quality/c28350)|La anotación describe una situación no aplicable de forma condicional.|
|[C28351](/cpp/code-quality/c28351)|La anotación describe dónde no se puede usar un valor dinámico (una variable) en la condición.|