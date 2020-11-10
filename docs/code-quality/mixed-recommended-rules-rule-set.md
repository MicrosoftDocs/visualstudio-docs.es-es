---
title: Conjunto de reglas Reglas recomendadas mixtas
ms.date: 11/04/2016
description: Obtenga información sobre el conjunto de reglas reglas recomendadas mixtas en Visual Studio. Vea las descripciones de las reglas para los proyectos de C++ compatibles con Common Language Runtime.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc30012dc025c5fc92f6d589c8e40740d689a86b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437075"
---
# <a name="mixed-recommended-rules-rule-set"></a>Conjunto de reglas Reglas recomendadas mixtas

Las reglas recomendadas mixtas de Microsoft se centran en los problemas más comunes y críticos en los proyectos de C++ compatibles con Common Language Runtime, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Este conjunto de reglas incluye todas las reglas del conjunto de reglas [reglas mínimas mixtas](mixed-minimum-rules-rule-set.md) .

Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para los proyectos de C++ compatibles con Common Language Runtime.

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
|[C6216](/cpp/code-quality/c6216)|Conversión de Compiler-Inserted no válida de BOOL a HRESULT|
|[C6217](/cpp/code-quality/c6217)|Prueba HRESULT no válida con NOT|
|[C6220](/cpp/code-quality/c6220)|Comparación de HRESULT no válida con-1|
|[C6226](/cpp/code-quality/c6226)|Asignación de HRESULT no válida a-1|
|[C6230](/cpp/code-quality/c6230)|Uso de HRESULT no válido como booleano|
|[C6235](/cpp/code-quality/c6235)|Constante distinta de cero con Logical-Or|
|[C6236](/cpp/code-quality/c6236)|Logical-Or con una constante distinta de cero|
|[C6237](/cpp/code-quality/c6237)|Cero con Logical-And pierde efectos secundarios|
|[C6242](/cpp/code-quality/c6242)|Desenredo local forzado|
|[C6248](/cpp/code-quality/c6248)|Creando DACL null|
|[C6250](/cpp/code-quality/c6250)|Descriptores de dirección no liberados|
|[C6255](/cpp/code-quality/c6255)|Uso no protegido de alloca|
|[C6258](/cpp/code-quality/c6258)|Usar el subproceso Terminate|
|[C6259](/cpp/code-quality/c6259)|Código muerto en Bitwise-Or conmutador limitado|
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
|[C6278](/cpp/code-quality/c6278)|Array-New Scalar-Delete no coinciden|
|[C6279](/cpp/code-quality/c6279)|Scalar-New Array-Delete no coinciden|
|[C6280](/cpp/code-quality/c6280)|Allocation-Deallocation de memoria no coincidente|
|[C6281](/cpp/code-quality/c6281)|Precedencia de relación bit a bit|
|[C6282](/cpp/code-quality/c6282)|La asignación reemplaza la prueba|
|[C6283](/cpp/code-quality/c6283)|Scalar-Delete de Array-New primitivos no coincidentes|
|[C6284](/cpp/code-quality/c6284)|Argumento de objeto no válido para la función de formato|
|[C6285](/cpp/code-quality/c6285)|Logical-Or de constantes|
|[C6286](/cpp/code-quality/c6286)|Logical-Or distinta de cero que pierden efectos secundarios|
|[C6287](/cpp/code-quality/c6287)|Prueba redundante|
|[C6288](/cpp/code-quality/c6288)|La inclusión mutua en Logical-And es falsa|
|[C6289](/cpp/code-quality/c6289)|La exclusión mutua en Logical-Or es true|
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
|[C6314](/cpp/code-quality/c6314)|Precedencia de Bitwise-Or|
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
|[C6383](/cpp/code-quality/c6383)|Element-Count saturación del búfer de Byte-Count|
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
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1009](../code-quality/ca1009.md)|Declarar los controladores de evento correctamente|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1049](../code-quality/ca1049.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|No ocultar métodos de clase base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementar IDisposable correctamente|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415.md)|Declarar elementos P/Invoke correctamente|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Quitar finalizadores vacíos|
|[CA1900](../code-quality/ca1900.md)|Los campos de tipo de valor deben ser portátiles|
|[CA1901](../code-quality/ca1901.md)|Las declaraciones P/Invoke deben ser portátiles|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|No bloquear objetos con identidad débil|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Especificar serialización en argumentos de cadena P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2111](../code-quality/ca2111.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2116](../code-quality/ca2116.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2122](../code-quality/ca2122.md)|No exponer indirectamente métodos con peticiones de vínculos|
|[CA2123](../code-quality/ca2123.md)|Las peticiones de vínculos de invalidaciones deben ser idénticas a la base|
|[CA2124](../code-quality/ca2124.md)|Incluir cláusulas finally vulnerables en un bloque try externo|
|[CA2126](../code-quality/ca2126.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2131](../code-quality/ca2131.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base|
|[CA2133](../code-quality/ca2133.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134.md)|Los métodos deben mantener una transparencia coherente al invalidar métodos base|
|[CA2137](../code-quality/ca2137.md)|Los métodos transparentes deben contener solo IL que se pueda comprobar|
|[CA2138](../code-quality/ca2138.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141.md)|Los métodos transparentes no deben satisfacer LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base|
|[CA2147](../code-quality/ca2147.md)|Los métodos transparentes no pueden usar aserciones de seguridad|
|[CA2149](../code-quality/ca2149.md)|Los métodos transparentes no deben llamar a código nativo|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Reiniciar para mantener los detalles de la pila|
|[CA2202](../code-quality/ca2202.md)|No usar Dispose varias veces en objetos|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Los campos descartables deben ser descartables|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|No llamar a métodos reemplazables en constructores|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementar constructores de serialización|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable correctamente|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Comprobar NaN correctamente|