---
title: "Conjunto de reglas Reglas recomendadas mixtas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3186b5b-0149-4a75-826e-e3539e4e703f
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de reglas Reglas recomendadas mixtas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las reglas mixtas recomendadas de Microsoft se centran en los problemas más graves y habituales de los proyectos de C\+\+ compatibles con Common Language Runtime, incluyendo posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores importantes de diseño y lógica.  Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos de C\+\+ compatibles con Common Language Runtime.  Este conjunto de reglas está diseñado para configurarse con Visual Studio Professional y versiones posteriores.  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[C6001](../code-quality/c6001.md)|Usar la Memoria sin inicializar.|  
|[C6011](../code-quality/c6011.md)|Desreferenciar el puntero nulo.|  
|[C6029](../code-quality/c6029.md)|Uso del valor sin comprobar.|  
|[C6031](../code-quality/c6031.md)|Valor devuelto omitido|  
|[C6053](../code-quality/c6053.md)|Terminación en cero de la llamada|  
|[C6054](../code-quality/c6054.md)|Falta de terminación en cero|  
|[C6059](../code-quality/c6059.md)|Concatenación incorrecta|  
|[C6063](../code-quality/c6063.md)|Argumento de cadena que falta para dar formato a la función|  
|[C6064](../code-quality/c6064.md)|Argumento entero ausente para dar formato a la función|  
|[C6066](../code-quality/c6066.md)|Argumento puntero ausente para dar formato a la función|  
|[C6067](../code-quality/c6067.md)|Argumento de puntero de cadena ausente para dar formato a la función|  
|[C6101](../code-quality/c6101.md)|Devolver la memoria no inicializada|  
|[C6200](../code-quality/c6200.md)|El índice supera el máximo del búfer|  
|[C6201](../code-quality/c6201.md)|El índice supera el máximo del búfer de pila|  
|[C6214](../code-quality/c6214.md)|Conversión no válida HRESULT a BOOL|  
|[C6215](../code-quality/c6215.md)|Conversión no válida BOOL a HRESULT|  
|[C6216](../code-quality/c6216.md)|Conversión insertada por compilador no válida BOOL a HRESULT|  
|[C6217](../code-quality/c6217.md)|Prueba HRESULT no válida con NOT|  
|[C6220](../code-quality/c6220.md)|HRESULT no válido en comparación con \-1|  
|[C6226](../code-quality/c6226.md)|Asignación no válida de HRESULT cómo \-1|  
|[C6230](../code-quality/c6230.md)|Uso no válido de HRESULT como booleano|  
|[C6235](../code-quality/c6235.md)|Constante distinta de cero con operador lógico Or|  
|[C6236](../code-quality/c6236.md)|Operador lógico Or con constante distinta de cero|  
|[C6237](../code-quality/c6237.md)|Cero con operador lógico AND pierde efectos secundarios|  
|[C6242](../code-quality/c6242.md)|Desenredo local forzado|  
|[C6248](../code-quality/c6248.md)|Crear una DACL Nula|  
|[C6250](../code-quality/c6250.md)|Descriptores inéditos de dirección|  
|[C6255](../code-quality/c6255.md)|Uso desprotegido de Alloca|  
|[C6258](../code-quality/c6258.md)|Usar el subproceso finalizar|  
|[C6259](../code-quality/c6259.md)|Código no alcanzado en interruptor limitado por operador en el nivel de bits Or|  
|[C6260](../code-quality/c6260.md)|Uso de la Aritmética de Byte|  
|[C6262](../code-quality/c6262.md)|Uso excesivo de pila|  
|[C6263](../code-quality/c6263.md)|Usar Alloca en bucle|  
|[C6268](../code-quality/c6268.md)|Faltan paréntesis en la conversión|  
|[C6269](../code-quality/c6269.md)|Puntero de desreferenciación omitido|  
|[C6270](../code-quality/c6270.md)|Falta el argumento Float para dar formato ala función|  
|[C6271](../code-quality/c6271.md)|Argumento adicional para dar formato a la función|  
|[C6272](../code-quality/c6272.md)|Argumento no Float para dar formato a la función|  
|[C6273](../code-quality/c6273.md)|Argumento no Entero para dar formato a la función|  
|[C6274](../code-quality/c6274.md)|Argumento no Carácter para dar formato a la función|  
|[C6276](../code-quality/c6276.md)|Conversión no válida de cadena|  
|[C6277](../code-quality/c6277.md)|Llamada no válida de CreateProcess|  
|[C6278](../code-quality/c6278.md)|No coincidencia de Matriz\-Nuevo Escalar\-Eliminar|  
|[C6279](../code-quality/c6279.md)|No coincidencia de Escalar\-Nueva Matriz\-Eliminar|  
|[C6280](../code-quality/c6280.md)|No coincidencia de Asignación\-Desasignación de memoria|  
|[C6281](../code-quality/c6281.md)|Precedencia de la relación de operador en el nivel de bits|  
|[C6282](../code-quality/c6282.md)|Asignación remplaza prueba|  
|[C6283](../code-quality/c6283.md)|Error de coincidencia en Matriz Primitiva\-Nuevo Escalar\-Eliminar|  
|[C6284](../code-quality/c6284.md)|Argumento objeto no válido para dar formato a la función|  
|[C6285](../code-quality/c6285.md)|Operador lógico Or de constantes|  
|[C6286](../code-quality/c6286.md)|Operador lógico Or distinto de cero que pierde efectos secundarios|  
|[C6287](../code-quality/c6287.md)|Prueba redundante|  
|[C6288](../code-quality/c6288.md)|Inclusión mutua del operador lógico AND es falsa|  
|[C6289](../code-quality/c6289.md)|La exclusión mutua sobre el operador lógico or es verdadera|  
|[C6290](../code-quality/c6290.md)|Prioridad entre operadores NOT lógico y AND bit a bit|  
|[C6291](../code-quality/c6291.md)|Prioridad entre operadores NOT lógico y OR bit a bit|  
|[C6292](../code-quality/c6292.md)|Recuento de un máximo de bucles|  
|[C6293](../code-quality/c6293.md)|Recuento de un mínimo de bucles|  
|[C6294](../code-quality/c6294.md)|Cuerpo del bucle nunca ejecutado|  
|[C6295](../code-quality/c6295.md)|Bucle infinito|  
|[C6296](../code-quality/c6296.md)|Bucle ejecutado una vez|  
|[C6297](../code-quality/c6297.md)|Resultado de la conversión con desplazamiento a un mayor tamaño|  
|[C6299](../code-quality/c6299.md)|Campo de bits a comparación booleana|  
|[C6302](../code-quality/c6302.md)|Argumento de cadena de carácter no válido para dar formato a la función|  
|[C6303](../code-quality/c6303.md)|Argumento de cadena de caracteres anchos no válido para dar formato a la función|  
|[C6305](../code-quality/c6305.md)|Error de coincidencia en tamaño y recuento de uso|  
|[C6306](../code-quality/c6306.md)|Llamada de función con argumento variable incorrecta|  
|[C6308](../code-quality/c6308.md)|Pérdidas por Realloc|  
|[C6310](../code-quality/c6310.md)|Constante no válida del filtro de excepciones|  
|[C6312](../code-quality/c6312.md)|Excepción bucle de ejecución continuo|  
|[C6314](../code-quality/c6314.md)|Precedencia del operador bit a bit Or|  
|[C6317](../code-quality/c6317.md)|Complemento No No|  
|[C6318](../code-quality/c6318.md)|Excepción continuar la búsqueda|  
|[C6319](../code-quality/c6319.md)|Omitido por coma|  
|[C6324](../code-quality/c6324.md)|Copia de la cadena en lugar de la comparación de la cadena|  
|[C6328](../code-quality/c6328.md)|Error de coincidencia de tipo de argumento potencial|  
|[C6331](../code-quality/c6331.md)|Marcas VirtualFree no válidas|  
|[C6332](../code-quality/c6332.md)|Parámetro no válido VirtualFree|  
|[C6333](../code-quality/c6333.md)|Tamaño no válido VirtualFree|  
|[C6335](../code-quality/c6335.md)|Controlador del proceso con pérdidas|  
|[C6381](../code-quality/c6381.md)|Falta de información de apagado|  
|[C6383](../code-quality/c6383.md)|Saturación del búfer de recuento de elemento y recuento de bytes|  
|[C6384](../code-quality/c6384.md)|División de tamaño de puntero|  
|[C6385](../code-quality/c6385.md)|Saturación de lectura|  
|[C6386](../code-quality/c6386.md)|Saturación de escritura|  
|[C6387](../code-quality/c6387.md)|Valor de parámetro no válido|  
|[C6388](../code-quality/c6388.md)|Valor de parámetro no válido|  
|[C6500](../code-quality/c6500.md)|Propiedad no válida del atributo|  
|[C6501](../code-quality/c6501.md)|Valores de propiedad de atributo en conflicto|  
|[C6503](../code-quality/c6503.md)|Las referencias no pueden ser nulas|  
|[C6504](../code-quality/c6504.md)|NULL en un no Puntero|  
|[C6505](../code-quality/c6505.md)|MustCheck en vacío|  
|[C6506](../code-quality/c6506.md)|Tamaño de búfer en no Puntero o matriz|  
|[C6507](http://msdn.microsoft.com/es-es/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Desigualdad Null en desreferenciación cero|  
|[C6508](../code-quality/c6508.md)|Acceso de escritura en constante|  
|[C6509](../code-quality/c6509.md)|Retorno utilizado en condición previa|  
|[C6510](../code-quality/c6510.md)|Null finalizado en no Puntero|  
|[C6511](../code-quality/c6511.md)|La propiedad MustCheck debe ser Sí o No|  
|[C6513](../code-quality/c6513.md)|Tamaño de elemento sin tamaño de búfer|  
|[C6514](../code-quality/c6514.md)|El tamaño de búfer supera el tamaño de la matriz|  
|[C6515](../code-quality/c6515.md)|Tamaño de búfer en no Puntero|  
|[C6516](../code-quality/c6516.md)|Ninguna propiedad en el atributo|  
|[C6517](../code-quality/c6517.md)|Tamaño válido en búfer no Legible|  
|[C6518](../code-quality/c6518.md)|Tamaño de escritura en búfer no modificable|  
|[C6519](http://msdn.microsoft.com/es-es/2b6326b0-0539-4d26-8fb1-720114933232)|Anotación inválida: el valor de propiedad 'NeedsRelease' debe ser Sí o No.|  
|[C6521](http://msdn.microsoft.com/es-es/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|Desreferenciación de la cadena de tamaño no válido|  
|[C6522](../code-quality/c6522.md)|Tipo tamaño de cadena no válido|  
|[C6523](http://msdn.microsoft.com/es-es/11397a31-b224-46b0-afb7-d49ca576a3bb)|Parámetro de cadena de tamaño no válido|  
|[C6525](../code-quality/c6525.md)|Ubicación inalcanzable de la cadena de tamaño no válida|  
|[C6526](http://msdn.microsoft.com/es-es/59c590c7-0098-4166-a1ac-87f324596002)|Tipo del búfer del tamaño de cadena no válido|  
|[C6527](../code-quality/c6527.md)|Anotación no válida: La propiedad 'NeedsRelease' no se puede utilizar en valores de tipo void|  
|[C6530](../code-quality/c6530.md)|Estilo desconocido del formato de la cadena|  
|[C6540](../code-quality/c6540.md)|El uso de anotaciones de atributo en esta función invalidará todas las anotaciones \_\_declspec existentes|  
|[C6551](../code-quality/c6551.md)|Especificación de tamaño no válida: expresión no analizable|  
|[C6552](../code-quality/c6552.md)|Deref\= no válida o Notref\=: expresión no analizable|  
|[C6701](../code-quality/c6701.md)|Este no es un valor Sí\/No\/Quizás válido|  
|[C6702](../code-quality/c6702.md)|El valor no es un valor de cadena|  
|[C6703](../code-quality/c6703.md)|El valor no es un número|  
|[C6704](../code-quality/c6704.md)|Error inesperado en la expresión de anotación|  
|[C6705](../code-quality/c6705.md)|El número esperado de argumentos para la anotación no coincide con el número real de argumentos para la anotación|  
|[C6706](../code-quality/c6706.md)|Error inesperado de Anotación para anotaciones|  
|[C6995](../code-quality/c6995.md)|No se pudo guardar el archivo de registro XML|  
|[C26100](../code-quality/c26100.md)|Condición de carrera|  
|[C26101](../code-quality/c26101.md)|La operación entrelazada no se usó correctamente|  
|[C26110](../code-quality/c26110.md)|El llamador no puede mantener el bloqueo|  
|[C26111](../code-quality/c26111.md)|El llamador no puede liberar el bloqueo|  
|[C26112](../code-quality/c26112.md)|El llamador no puede mantener ningún bloqueo|  
|[C26115](../code-quality/c26115.md)|Error al liberar el bloqueo|  
|[C26116](../code-quality/c26116.md)|Error al adquirir o mantener el bloqueo|  
|[C26117](../code-quality/c26117.md)|Liberar el bloqueo no retenido|  
|[C26140](../code-quality/c26140.md)|Error de anotación SAL de simultaneidad|  
|[C28020](../code-quality/c28020.md)|La expresión no es verdadera en esta llamada.|  
|[C28021](../code-quality/c28021.md)|El parámetro anotado debe ser un puntero|  
|[C28022](../code-quality/c28022.md)|Las clases de función de esta función no coinciden con las clases de función del typedef usado para definirla.|  
|[C28023](../code-quality/c28023.md)|La función que se va a asignar o pasar debe tener una anotación \_Function\_class\_ para al menos una de las clases|  
|[C28024](../code-quality/c28024.md)|El puntero a función al que se asigna tiene anotada la clase de función, no incluida en la lista de clases de funciones.|  
|[C28039](../code-quality/c28039.md)|El tipo del parámetro actual debe coincidir exactamente con el tipo|  
|[C28112](../code-quality/c28112.md)|A una variable a la que se tiene acceso mediante una función Interlocked siembre se debe obtener acceso mediante una función Interlocked.|  
|[C28113](../code-quality/c28113.md)|Acceso a una variable local mediante una función Interlocked|  
|[C28125](../code-quality/c28125.md)|Debe llamarse a la función desde un bloque try\/except|  
|[C28137](../code-quality/c28137.md)|La variable de argumento debería ser una constante \(literal\)|  
|[C28138](../code-quality/c28138.md)|Los argumentos constantes deberían ser variables|  
|[C28159](../code-quality/c28159.md)|Considere utilizar otra función en su lugar.|  
|[C28160](../code-quality/c28160.md)|anotación Error|  
|[C28163](../code-quality/c28163.md)|No debe llamarse nunca a la función desde un bloque try\/except|  
|[C28164](../code-quality/c28164.md)|El argumento se está pasando a una función que espera un puntero a un objeto \(no un puntero a un puntero\)|  
|[C28182](../code-quality/c28182.md)|Desreferenciando el puntero NULL.  El puntero contiene el mismo valor NULL que otro puntero.|  
|[C28183](../code-quality/c28183.md)|El argumento no puede ser un valor, y es una copia del valor encontrado en el puntero|  
|[C28193](../code-quality/c28193.md)|La variable contiene un valor que debe ser examinado|  
|[C28196](../code-quality/c28196.md)|El requisito no se cumple. \(La expresión no se evalúa como true.\)|  
|[C28202](../code-quality/c28202.md)|Referencia no válida a un miembro no estático.|  
|[C28203](../code-quality/c28203.md)|Referencia ambigua a un miembro de clase.|  
|[C28205](../code-quality/c28205.md)|Se usó \_Success\_ u \_On\_failure\_ en un contexto no válido|  
|[C28206](../code-quality/c28206.md)|Puntos izquierdo del operando un struct, use “\-\>”|  
|[C28207](../code-quality/c28207.md)|El operando izquierdo es un struct, use '.'|  
|[C28209](../code-quality/c28209.md)|La declaración del símbolo tiene una declaración en conflicto|  
|[C28220](../code-quality/c28210.md)|Las anotaciones para el contexto \_on\_failure\_ no deben estar en un contexto previo explícito:|  
|[C28211](../code-quality/c28211.md)|Se esperaba un nombre de contexto estático para SAL\_context.|  
|[C28212](../code-quality/c28212.md)|Expresión de puntero esperada para la anotación|  
|[C28213](../code-quality/c28213.md)|La anotación \_Use\_decl\_annotations\_ se debe usar para hacer referencia, sin modificación, a una declaración anterior.|  
|[C28214](../code-quality/c28214.md)|Los nombres de atributo de parámetros deben ser p1...p9|  
|[C28215](../code-quality/c28215.md)|typefix no se puede aplicar a un parámetro que ya tenga un typefix|  
|[C28216](../code-quality/c28216.md)|La anotación de checkReturn solicita solo a las condiciones posteriores el parámetro de la función específica.|  
|[C28217](../code-quality/c28217.md)|Para la función, el número de parámetros para la anotación no coincide con el encontrado en el archivo.|  
|[C28218](../code-quality/c28218.md)|Para el parámetro de la función, el parámetro de anotación no coincide con el que se ha encontrado en el archivo|  
|[C28219](../code-quality/c28219.md)|Se esperaba un miembro de enumeración para el parámetro de la anotación|  
|[C28220](../code-quality/c28220.md)|Expresión de entero esperada para anotación el parámetro en la anotación|  
|[C28221](../code-quality/c28221.md)|Expresión de cadena esperada para el parámetro en la anotación|  
|[C28222](../code-quality/c28222.md)|\_\_si, \_\_no, or \_\_quizás esperado para la anotación|  
|[C28223](../code-quality/c28223.md)|No se encontró el token o identificador esperado para el parámetro de la anotación|  
|[C28224](../code-quality/c28224.md)|La anotación requiere parámetros|  
|[C28225](../code-quality/c28225.md)|No se encontró el número correcto de parámetros requeridos en la anotación|  
|[C28226](../code-quality/c28226.md)|La anotación no puede ser también un elemento PrimOp \(en la declaración actual\)|  
|[C28227](../code-quality/c28227.md)|La anotación no puede ser también un elemento PrimOp \(ver declaración anterior\)|  
|[C28228](../code-quality/c28228.md)|Parámetro de anotación: no puede utilizar tipos en anotaciones|  
|[C28229](../code-quality/c28229.md)|La anotación no admite parámetros.|  
|[C28230](../code-quality/c28230.md)|El tipo de parámetro no tiene ningún miembro.|  
|[C28231](../code-quality/c28231.md)|La anotación sólo es válida en la matriz|  
|[C28232](../code-quality/c28232.md)|pre, post o deref no se aplican a ninguna anotación|  
|[C28233](../code-quality/c28233.md)|pre, post o deref se aplican a un bloque|  
|[C28234](../code-quality/c28234.md)|La expresión \_\_at no se aplica a la función actual|  
|[C28235](../code-quality/c28235.md)|La función no puede usarse de forma independiente como anotación|  
|[C28236](../code-quality/c28236.md)|La anotación no se puede usar en una expresión|  
|[C28237](../code-quality/c28237.md)|Ya no se admite la anotación en el parámetro|  
|[C28238](../code-quality/c28238.md)|La anotación en el parámetro tiene más de un elemento value, stringValue y longValue.  Use paramn\=xxx|  
|[C28239](../code-quality/c28239.md)|la anotación en el parámetro tiene tanto un elemento value como stringValue o longValue, además de paramn\=xxx.  Use solamente paramn\=xxx.|  
|[C28240](../code-quality/c28240.md)|La anotación en el parámetro tiene un elemento param2 pero no param1|  
|[C28241](../code-quality/c28241.md)|La anotación para la función de parámetro no se reconoce|  
|[C28243](../code-quality/c28243.md)|La anotación de la función en el parámetro requiere más desreferencias de las que permite el tipo anotado real.|  
|[C28244](../code-quality/c28244.md)|La anotación de la función tiene un parámetro o anotación externa que no se puede analizar.|  
|[C28245](../code-quality/c28245.md)|La anotación de la función anota 'this' en una función no miembro.|  
|[C28246](../code-quality/c28246.md)|La anotación de parámetro para función no coincide con el tipo de parámetro|  
|[C28250](../code-quality/c28250.md)|Anotación incoherente para la función: la instancia anterior tiene un error.|  
|[C28251](../code-quality/c28251.md)|Anotación incoherente para la función: esta instancia tiene un error.|  
|[C28252](../code-quality/c28252.md)|Anotación incoherente para la función: el parámetro tiene otras anotaciones en esta instancia.|  
|[C28253](../code-quality/c28253.md)|Anotación incoherente para la función: el parámetro tiene otras anotaciones en esta instancia.|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast\<\>\(\) no se admite en anotaciones|  
|[C28262](../code-quality/c28262.md)|Se encontró un error de sintaxis de anotación en la función, para la anotación|  
|[C28263](../code-quality/c28263.md)|Se encontró un error de sintaxis en una anotación condicional para la anotación de tipo intrínseco|  
|[C28264](http://msdn.microsoft.com/es-es/bf6ea983-a06e-4752-a042-747a7dbf338c)|Los valores de las listas de resultados deben ser constantes.|  
|[C28267](../code-quality/c28267.md)|Se encontró un error de sintaxis de anotaciones en la función para la anotación.|  
|[C28272](../code-quality/c28272.md)|El parámetro de la anotación de la función al examinar no es coherente con la declaración de la función|  
|[C28273](../code-quality/c28273.md)|Para la función, las pistas no son coherentes con la declaración de la función|  
|[C28275](../code-quality/c28275.md)|El parámetro para \_Macro\_value\_ es nulo|  
|[C28279](../code-quality/c28279.md)|Para el símbolo, se encontró un elemento 'begin' sin el elemento 'end' correspondiente|  
|[C28280](../code-quality/c28280.md)|Para el símbolo se encontró un elemento 'end' sin el elemento 'begin' correspondiente|  
|[C28282](../code-quality/c28282.md)|Las cadenas de formato deben estar en las condiciones previas|  
|[C28285](../code-quality/c28285.md)|Para la función, error de sintaxis en parámetro|  
|[C28286](../code-quality/c28286.md)|Para la función, error de sintaxis cerca del final|  
|[C28287](../code-quality/c28287.md)|Para la función, error de sintaxis en la anotación \_At\_\(\) \(nombre de parámetro no reconocido\)|  
|[C28288](../code-quality/c28288.md)|Para la función, error de sintaxis en la anotación \_At\_\(\) \(nombre de parámetro no válido\)|  
|[C28289](../code-quality/c28289.md)|Para la función: ReadableTo o WritableTo no tenían una especificación de límite como parámetro|  
|[C28290](../code-quality/c28290.md)|La anotación de la función contiene más valores External que el número real de parámetros|  
|[C28291](../code-quality/c28291.md)|null\/notnull posterior en el nivel 0 de desreferenciación carece de sentido para la función.|  
|[C28300](../code-quality/c28300.md)|Los operandos de expresión de tipos no son compatibles para el operador|  
|[C28301](../code-quality/c28301.md)|Ninguna anotación para la primera declaración de la función.|  
|[C28302](../code-quality/c28302.md)|Se encontró un operador adicional de \_Deref\_ en la anotación.|  
|[C28303](../code-quality/c28303.md)|Se encontró un operador ambiguo de \_Deref\_ en la anotación.|  
|[C28304](../code-quality/c28304.md)|Se encontró un operador incorrectamente colocado de \_Notref\_ aplicado al token.|  
|[C28305](../code-quality/c28305.md)|Se detectó un error mientras analizaba un token.|  
|[C28306](../code-quality/c28306.md)|La anotación en parámetro es obsoleta|  
|[C28307](../code-quality/c28307.md)|La anotación en parámetro es obsoleta|  
|[C28350](../code-quality/c28350.md)|La anotación describe una situación no aplicable de forma condicional.|  
|[C28351](../code-quality/c28351.md)|La anotación describe dónde no se puede usar un valor dinámico \(una variable\) en la condición.|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declare los controladores de evento correctamente|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar los ensamblados con AssemblyVersionAttribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Los tipos secundarios deberían poder llamar a los métodos de interfaz|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Los tipos que poseen recursos nativos deben ser descartables|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mueva P\/Invokes a la clase NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|No oculte métodos de clases base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implemente IDisposable correctamente|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|No producir excepciones en ubicaciones inesperadas|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Deben existir puntos de entrada P\/Invoke|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Los elementos P\/Invoke no deben estar visibles|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Los tipos de diseño automático no deben ser visibles para COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Llame a GetLastError inmediatamente después de P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Los tipos base de tipos visibles para COM deben ser visibles para COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Los métodos de registro COM se deben adjuntar|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declare los elementos P\/Invoke correctamente|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar los finalizadores vacíos|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Los campos de tipos de valor deberían ser portátiles|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Las declaraciones P\/Invoke deben ser portátiles|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|No bloquear objetos con identidad débil|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revisar las consultas SQL en busca de vulnerabilidades de seguridad|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique cálculo de referencias para argumentos de cadena P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revisar la seguridad declarativa en los tipos de valor|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Los punteros no deberían estar visibles|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Los tipos seguros no deberían exponer campos|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La seguridad del método debería ser un supraconjunto del tipo|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Los métodos APTCA deben llamar solo a métodos APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Los tipos APTCA solo amplían tipos base APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|No exponer indirectamente métodos con peticiones de vínculos|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Las peticiones de vínculos de remplazo deberían ser idénticas a la base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluir cláusulas Finally vulnerables en un bloque Try externo|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Las peticiones de tipo vínculos requieren peticiones de herencias|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base.|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Los métodos deben mantener una transparencia coherente cuando remplazan métodos base|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Los métodos transparentes deben contener solo IL que se puedan comprobar|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Los métodos transparentes no deben satisfacer LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base.|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Los métodos transparentes no pueden usar aserciones de seguridad|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Los métodos transparentes no deben llamar a código nativo|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Iniciar de nuevo para preservar los detalles de la pila|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|No desechar objetos varias veces|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de valor alineados|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|No marcar los componentes servidos como WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos desechables se deben desechar|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|No llamar a métodos reemplazables en constructores|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Los tipos descartables deben declarar el finalizador|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Los finalizadores deben llamar al finalizador de la clase base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementar constructores de serialización|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador de igualdad al remplazar el tipo de valor de igualdad|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Marcar puntos de entrada de Windows Forms con STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos los campos no serializables|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Llamar a métodos de clase base en tipos ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar los tipos ISerializable con SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar los métodos de serialización de forma correcta|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementar ISerializable correctamente|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Proporcionar argumentos correctos a los métodos de formato|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Prueba para NaN correcta|