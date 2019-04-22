---
title: Conjunto de reglas reglas mínimas mixtas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fbc8239fc3472d5dd5e8a24ca2b0c125d57cca21
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653078"
---
# <a name="mixed-minimum-rules-rule-set"></a>Conjunto de reglas Reglas mínimas mixtas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La reglas mínimas mixtas de Microsoft se centran en los problemas más graves en los proyectos de C++ compatibles con Common Language Runtime, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos de C++ compatibles con Common Language Runtime.  

|                                            Regla                                             |                                                  Descripción                                                  |
|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                              [C6001](../code-quality/c6001.md)                              |                                          Uso de la memoria sin inicializar                                           |
|                              [C6011](../code-quality/c6011.md)                              |                                          Desreferenciación de un puntero null                                           |
|                              [C6029](../code-quality/c6029.md)                              |                                            Uso de un valor sin comprobar                                             |
|                              [C6053](../code-quality/c6053.md)                              |                                          Terminación en cero de la llamada                                           |
|                              [C6059](../code-quality/c6059.md)                              |                                               Concatenación incorrecta                                               |
|                              [C6063](../code-quality/c6063.md)                              |                                  Falta el argumento de cadena para la función de formato                                   |
|                              [C6064](../code-quality/c6064.md)                              |                                  Falta el argumento de entero para la función de formato                                  |
|                              [C6066](../code-quality/c6066.md)                              |                                  Falta el argumento de puntero para la función de formato                                  |
|                              [C6067](../code-quality/c6067.md)                              |                              Falta el argumento de puntero de cadena para la función de formato                               |
|                              [C6101](../code-quality/c6101.md)                              |                                        Devolución de memoria sin inicializar                                         |
|                              [C6200](../code-quality/c6200.md)                              |                                         El índice supera el valor máximo para el búfer                                          |
|                              [C6201](../code-quality/c6201.md)                              |                                      El índice supera el valor máximo para el búfer de pila                                       |
|                              [C6270](../code-quality/c6270.md)                              |                                   Falta el argumento float para la función de formato                                   |
|                              [C6271](../code-quality/c6271.md)                              |                                       Argumento adicional para la función de formato                                       |
|                              [C6272](../code-quality/c6272.md)                              |                                     Argumento no flotante para la función de formato                                     |
|                              [C6273](../code-quality/c6273.md)                              |                                    Argumento no entero para la función de formato                                     |
|                              [C6274](../code-quality/c6274.md)                              |                                   Argumento sin caracteres para la función de formato                                   |
|                              [C6276](../code-quality/c6276.md)                              |                                              Conversión de cadena no válida                                              |
|                              [C6277](../code-quality/c6277.md)                              |                                          Llamada no válida a CreateProcess                                           |
|                              [C6284](../code-quality/c6284.md)                              |                                  Argumento de objeto no válido para la función de formato                                   |
|                              [C6290](../code-quality/c6290.md)                              |                                      Prioridad entre operadores NOT lógico y AND bit a bit                                       |
|                              [C6291](../code-quality/c6291.md)                              |                                       Prioridad entre operadores NOT lógico y OR bit a bit                                       |
|                              [C6302](../code-quality/c6302.md)                              |                             Argumento de cadena de caracteres no válido para la función de formato                              |
|                              [C6303](../code-quality/c6303.md)                              |                           Argumento de cadena de caracteres anchos no válido para la función de formato                           |
|                              [C6305](../code-quality/c6305.md)                              |                                         Error de coincidencia en el uso de size y count                                         |
|                              [C6306](../code-quality/c6306.md)                              |                                   Llamada incorrecta a función de argumento variable                                   |
|                              [C6328](../code-quality/c6328.md)                              |                                       Error de coincidencia de tipo de argumento potencial                                        |
|                              [C6385](../code-quality/c6385.md)                              |                                                 Saturación de lectura                                                  |
|                              [C6386](../code-quality/c6386.md)                              |                                                 Saturación de escritura                                                 |
|                              [C6387](../code-quality/c6387.md)                              |                                            Valor de parámetro no válido                                            |
|                              [C6500](../code-quality/c6500.md)                              |                                          Propiedad de atributo no válida                                           |
|                              [C6501](../code-quality/c6501.md)                              |                                     Valores de propiedad de atributo en conflicto                                     |
|                              [C6503](../code-quality/c6503.md)                              |                                           Las referencias no pueden ser null                                           |
|                              [C6504](../code-quality/c6504.md)                              |                                              Null en valores que no son de puntero                                              |
|                              [C6505](../code-quality/c6505.md)                              |                                               MustCheck en valores void                                               |
|                              [C6506](../code-quality/c6506.md)                              |                                      Tamaño de búfer en valores que no son de puntero o matriz                                      |
|        [C6507](http://msdn.microsoft.com/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       No coincidencia Null en desreferenciación cero                                       |
|                              [C6508](../code-quality/c6508.md)                              |                                           Acceso de escritura en valores constantes                                            |
|                              [C6509](../code-quality/c6509.md)                              |                                          Return usado en condición previa                                          |
|                              [C6510](../code-quality/c6510.md)                              |                                        NullTerminated en valores que no son de puntero                                         |
|                              [C6511](../code-quality/c6511.md)                              |                                          MustCheck debe ser Yes o No                                          |
|                              [C6513](../code-quality/c6513.md)                              |                                       ElementSize sin tamaño de búfer                                        |
|                              [C6514](../code-quality/c6514.md)                              |                                        El tamaño del búfer supera el tamaño de la matriz                                         |
|                              [C6515](../code-quality/c6515.md)                              |                                          Tamaño de búfer en valores que no son de puntero                                           |
|                              [C6516](../code-quality/c6516.md)                              |                                          No hay propiedades del atributo                                           |
|                              [C6517](../code-quality/c6517.md)                              |                                       Tamaño válido en búfer no legible                                       |
|                              [C6518](../code-quality/c6518.md)                              |                                     Tamaño de escritura en búfer no modificable                                      |
|        [C6521](http://msdn.microsoft.com/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)        |                                        Desreferenciación de cadena de tamaño no válida                                        |
|                              [C6522](../code-quality/c6522.md)                              |                                           Tipo de cadena de tamaño no válido                                            |
|        [C6523](http://msdn.microsoft.com/11397a31-b224-46b0-afb7-d49ca576a3bb)        |                                         Parámetro de cadena de tamaño no válido                                         |
|                              [C6525](../code-quality/c6525.md)                              |                                   Cadena de tamaño no válida, ubicación inaccesible                                    |
|        [C6526](http://msdn.microsoft.com/59c590c7-0098-4166-a1ac-87f324596002)        |                                        Tipo de búfer de cadena de tamaño no válido                                        |
|                              [C6527](../code-quality/c6527.md)                              |              Anotación no válida: Propiedad 'NeedsRelease' no puede usarse en los valores de tipo void               |
|                              [C6530](../code-quality/c6530.md)                              |                                       Estilo de cadena de formato no reconocido                                        |
|                              [C6540](../code-quality/c6540.md)                              | El uso de anotaciones de atributo en esta función invalidará todas las anotaciones __declspec existentes  |
|                              [C6551](../code-quality/c6551.md)                              |                              Especificación de tamaño no válido: no se puede analizar la expresión                              |
|                              [C6552](../code-quality/c6552.md)                              |                              Valor Deref= o Notref= no válido: no se puede analizar la expresión                               |
|                              [C6701](../code-quality/c6701.md)                              |                                  Este no es un valor Yes/No/Maybe válido                                  |
|                              [C6702](../code-quality/c6702.md)                              |                                        Este no es un valor de cadena                                        |
|                              [C6703](../code-quality/c6703.md)                              |                                           El valor no es un número                                           |
|                              [C6704](../code-quality/c6704.md)                              |                                    Error de expresión de anotación inesperado                                     |
|                              [C6705](../code-quality/c6705.md)                              |     El número esperado de argumentos para la anotación no coincide con el número real de argumentos para la anotación      |
|                              [C6706](../code-quality/c6706.md)                              |                                  Error inesperado de la anotación                                   |
|                             [C28021](../code-quality/c28021.md)                             |                                El parámetro que se va a anotar debe ser un puntero                                |
|                             [C28182](../code-quality/c28182.md)                             |         Desreferenciación de un puntero null. El puntero contiene el mismo valor NULL que otro puntero.          |
|                             [C28202](../code-quality/c28202.md)                             |                                    Referencia no válida a un miembro no estático                                     |
|                             [C28203](../code-quality/c28203.md)                             |                                     Referencia ambigua a un miembro de la clase.                                      |
|                             [C28205](../code-quality/c28205.md)                             |                           \_Success\_ o \_On_failure\_ usados en un contexto no válido                            |
|                             [C28206](../code-quality/c28206.md)                             |                                   El operando izquierdo señala a un struct, use '->'                                   |
|                             [C28207](../code-quality/c28207.md)                             |                                       El operando izquierdo es un struct, use '->'                                       |
|                             [C28210](../code-quality/c28210.md)                             |                 Las anotaciones del contexto __on_failure no deben estar en un contexto previo explícito                  |
|                             [C28211](../code-quality/c28211.md)                             |                                 Se esperaba un nombre de contexto estático para SAL_context                                  |
|                             [C28212](../code-quality/c28212.md)                             |                                  Se esperaba una expresión de puntero para la anotación                                   |
|                             [C28213](../code-quality/c28213.md)                             | La anotación \_Use_decl_annotations\_ se debe usar para hacer referencia, sin modificación, a una declaración anterior. |
|                             [C28214](../code-quality/c28214.md)                             |                                   Los nombres de los parámetros de atributo deben ser p1...p9                                   |
|                             [C28215](../code-quality/c28215.md)                             |                    typefix no se puede aplicar a un parámetro que ya tenga un typefix                    |
|                             [C28216](../code-quality/c28216.md)                             |        La anotación checkReturn solamente se aplica a las condiciones posteriores del parámetro de la función específica.         |
|                             [C28217](../code-quality/c28217.md)                             |            Para la función, el número de parámetros de la anotación no coincide con el encontrado en el archivo             |
|                             [C28218](../code-quality/c28218.md)                             |             Para el parámetro de función, el parámetro de la anotación no coincide con el encontrado en el archivo              |
|                             [C28219](../code-quality/c28219.md)                             |                 Se esperaba un miembro de enumeración para el parámetro de la anotación                 |
|                             [C28220](../code-quality/c28220.md)                             |                  Se esperaba una expresión de entero para el parámetro de la anotación                   |
|                             [C28221](../code-quality/c28221.md)                             |                        Se esperaba una expresión de cadena para el parámetro de la anotación                         |
|                             [C28222](../code-quality/c28222.md)                             |                               Se esperaba __yes, \__no, o \__maybe para la anotación                               |
|                             [C28223](../code-quality/c28223.md)                             |                       No se encontró el token o identificador para la anotación, parámetro                        |
|                             [C28224](../code-quality/c28224.md)                             |                                        La anotación requiere parámetros                                         |
|                             [C28225](../code-quality/c28225.md)                             |                     No se encontró el número correcto de parámetros necesarios en la anotación                      |
|                             [C28226](../code-quality/c28226.md)                             |                          La anotación no puede ser un PrimOp (en la declaración actual)                          |
|                             [C28227](../code-quality/c28227.md)                             |                          La anotación no puede ser un PrimOp (consulte la declaración anterior)                           |
|                             [C28228](../code-quality/c28228.md)                             |                             Parámetro de anotación: no se puede usar un tipo en las anotaciones                              |
|                             [C28229](../code-quality/c28229.md)                             |                                    La anotación no admite parámetros                                     |
|                             [C28230](../code-quality/c28230.md)                             |                                     El tipo de parámetro no tiene ningún miembro.                                      |
|                             [C28231](../code-quality/c28231.md)                             |                                       La anotación solo es válida en la matriz                                       |
|                             [C28232](../code-quality/c28232.md)                             |                               pre, post o deref no se aplican a ninguna anotación                               |
|                             [C28233](../code-quality/c28233.md)                             |                                    pre, post o deref se aplican a un bloque                                     |
|                             [C28234](../code-quality/c28234.md)                             |                              La expresión __at no se aplica a la función actual                               |
|                             [C28235](../code-quality/c28235.md)                             |                               La función no puede actuar por sí sola como una anotación                                |
|                             [C28236](../code-quality/c28236.md)                             |                                La anotación no se puede usar en una expresión                                 |
|                             [C28237](../code-quality/c28237.md)                             |                              La anotación del parámetro ya no se admite                               |
|                             [C28238](../code-quality/c28238.md)                             |      La anotación del parámetro tiene más de un valor, stringValue y longValue Use paramn=xxx       |
|                             [C28239](../code-quality/c28239.md)                             |  La anotación del parámetro tiene el valor stringValue o longValue, y paramn=xxx. Use solo paramn=xxx   |
|                             [C28240](../code-quality/c28240.md)                             |                             La anotación del parámetro tiene param2 pero no param1                              |
|                             [C28241](../code-quality/c28241.md)                             |                          La anotación para la función del parámetro no se reconoce                           |
|                             [C28243](../code-quality/c28243.md)                             |   La anotación para la función del parámetro requiere más desreferenciaciones de las que permite el tipo real anotado   |
|                             [C28245](../code-quality/c28245.md)                             |                     La anotación para la función anota 'this' en una en una función no miembro                     |
|                             [C28246](../code-quality/c28246.md)                             |                La anotación del parámetro para la función no coincide con el tipo del parámetro                 |
|                             [C28250](../code-quality/c28250.md)                             |                    Anotación incoherente de la función: la instancia anterior tiene un error.                     |
|                             [C28251](../code-quality/c28251.md)                             |                       Anotación incoherente de la función: esta instancia tiene un error.                       |
|                             [C28252](../code-quality/c28252.md)                             |           Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.           |
|                             [C28253](../code-quality/c28253.md)                             |           Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.           |
|                             [C28254](../code-quality/c28254.md)                             |                               dynamic_cast<>() no se admite en anotaciones                                |
|                             [C28262](../code-quality/c28262.md)                             |                    Se encontró un error de sintaxis de anotación en la función, para la anotación                     |
|                             [C28263](../code-quality/c28263.md)                             |                 Se encontró un error de sintaxis en una anotación condicional para la anotación intrínseca                 |
|                             [C28267](../code-quality/c28267.md)                             |                    Se encontró un error de sintaxis de anotaciones en la función.                    |
|                             [C28272](../code-quality/c28272.md)                             |      La anotación del parámetro de la función, al examinar su incoherencia con la declaración de la función      |
|                             [C28273](../code-quality/c28273.md)                             |                    Para la función, las pistas son incoherentes con la declaración de la función                     |
|                             [C28275](../code-quality/c28275.md)                             |                                   El parámetro para \_Macro_value\_ es null                                    |
|                             [C28279](../code-quality/c28279.md)                             |                           Para el símbolo, se encontró un 'begin' sin un 'end' coincidente                            |
|                             [C28280](../code-quality/c28280.md)                             |                           Para el símbolo, se encontró un 'end' sin un 'begin' coincidente                           |
|                             [C28282](../code-quality/c28282.md)                             |                                    Las cadenas de formato deben estar en las condiciones previas                                    |
|                             [C28285](../code-quality/c28285.md)                             |                                    Para la función, error de sintaxis en el parámetro                                    |
|                             [C28286](../code-quality/c28286.md)                             |                                    Para la función, error de sintaxis cerca del final                                    |
|                             [C28287](../code-quality/c28287.md)                             |                Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no reconocido)                |
|                             [C28288](../code-quality/c28288.md)                             |                  Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no válido)                   |
|                             [C28289](../code-quality/c28289.md)                             |                Para que funcione: ReadableTo o WritableTo no tenía una especificación de límite como parámetro                |
|                             [C28290](../code-quality/c28290.md)                             |           la anotación de la función contiene más valores External que el número real de parámetros            |
|                             [C28291](../code-quality/c28291.md)                             |                        El valor null/notnull posterior en el nivel 0 de desreferenciación carece de sentido para la función.                        |
|                             [C28300](../code-quality/c28300.md)                             |                            Operandos de expresión de tipos no compatibles para el operador                             |
|                             [C28301](../code-quality/c28301.md)                             |                               No hay anotaciones para la primera declaración de la función.                               |
|                             [C28302](../code-quality/c28302.md)                             |                             Se encontró un operador \_Deref\_ adicional en la anotación.                              |
|                             [C28303](../code-quality/c28303.md)                             |                           Se encontró un operador \_Deref\_ ambiguo en la anotación.                            |
|                             [C28304](../code-quality/c28304.md)                             |                     Se encontró un operador \_Notref\_ mal colocado aplicado al token.                      |
|                             [C28305](../code-quality/c28305.md)                             |                                Se descubrió un error al analizar un token.                                 |
|                             [C28350](../code-quality/c28350.md)                             |                  La anotación describe una situación no aplicable de forma condicional.                   |
|                             [C28351](../code-quality/c28351.md)                             |         La anotación describe dónde no se puede usar un valor dinámico (una variable) en la condición.          |
|  [CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  |                             Los tipos que poseen campos descartables deben ser descartables                             |
|                 [CA1821](../code-quality/ca1821-remove-empty-finalizers.md)                 |                                            Quitar finalizadores vacíos                                            |
|          [CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)           |                                     Los campos descartables deben ser descartables                                      |
| [CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) |                            Sobrecargar el operador equals al invalidar ValueType.Equals                            |
