---
title: "Conjunto de reglas Reglas m&#237;nimas nativas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de reglas Reglas m&#237;nimas nativas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El foco de reglas mínimos nativo de Microsoft en los problemas más importantes del código nativo, incluidos los vulnerabilidades de seguridad y bloqueos potenciales de la aplicación.  Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[C6001](../code-quality/c6001.md)|Usar la Memoria sin inicializar.|  
|[C6011](../code-quality/c6011.md)|Desreferenciar el puntero nulo.|  
|[C6029](../code-quality/c6029.md)|Uso del valor sin comprobar.|  
|[C6053](../code-quality/c6053.md)|Terminación en cero de la llamada|  
|[C6059](../code-quality/c6059.md)|Concatenación incorrecta|  
|[C6063](../code-quality/c6063.md)|Argumento de cadena que falta para dar formato a la función|  
|[C6064](../code-quality/c6064.md)|Argumento entero ausente para dar formato a la función|  
|[C6066](../code-quality/c6066.md)|Argumento puntero ausente para dar formato a la función|  
|[C6067](../code-quality/c6067.md)|Argumento de puntero de cadena ausente para dar formato a la función|  
|[C6101](../code-quality/c6101.md)|Devolver la memoria no inicializada|  
|[C6200](../code-quality/c6200.md)|El índice supera el máximo del búfer|  
|[C6201](../code-quality/c6201.md)|El índice supera el máximo del búfer de pila|  
|[C6270](../code-quality/c6270.md)|Falta el argumento Float para dar formato ala función|  
|[C6271](../code-quality/c6271.md)|Argumento adicional para dar formato a la función|  
|[C6272](../code-quality/c6272.md)|Argumento no Float para dar formato a la función|  
|[C6273](../code-quality/c6273.md)|Argumento no Entero para dar formato a la función|  
|[C6274](../code-quality/c6274.md)|Argumento no Carácter para dar formato a la función|  
|[C6276](../code-quality/c6276.md)|Conversión no válida de cadena|  
|[C6277](../code-quality/c6277.md)|Llamada no válida de CreateProcess|  
|[C6284](../code-quality/c6284.md)|Argumento objeto no válido para dar formato a la función|  
|[C6290](../code-quality/c6290.md)|Prioridad entre operadores NOT lógico y AND bit a bit|  
|[C6291](../code-quality/c6291.md)|Prioridad entre operadores NOT lógico y OR bit a bit|  
|[C6302](../code-quality/c6302.md)|Argumento de cadena de carácter no válido para dar formato a la función|  
|[C6303](../code-quality/c6303.md)|Argumento de cadena de caracteres anchos no válido para dar formato a la función|  
|[C6305](../code-quality/c6305.md)|Error de coincidencia en tamaño y recuento de uso|  
|[C6306](../code-quality/c6306.md)|Llamada de función con argumento variable incorrecta|  
|[C6328](../code-quality/c6328.md)|Error de coincidencia de tipo de argumento potencial|  
|[C6385](../code-quality/c6385.md)|Saturación de lectura|  
|[C6386](../code-quality/c6386.md)|Saturación de escritura|  
|[C6387](../code-quality/c6387.md)|Valor de parámetro no válido|  
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
|[C28021](../code-quality/c28021.md)|El parámetro anotado debe ser un puntero|  
|[C28182](../code-quality/c28182.md)|Desreferenciando el puntero NULL.  El puntero contiene el mismo valor NULL que otro puntero.|  
|[C28202](../code-quality/c28202.md)|Referencia no válida a un miembro no estático.|  
|[C28203](../code-quality/c28203.md)|Referencia ambigua a un miembro de clase.|  
|[C28205](../code-quality/c28205.md)|Se usó \_Success\_ u \_On\_failure\_ en un contexto no válido|  
|[C28206](../code-quality/c28206.md)|Puntos izquierdo del operando un struct, use “\-\>”|  
|[C28207](../code-quality/c28207.md)|El operando izquierdo es un struct, use '.'|  
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
|[C28350](../code-quality/c28350.md)|La anotación describe una situación no aplicable de forma condicional.|  
|[C28351](../code-quality/c28351.md)|La anotación describe dónde no se puede usar un valor dinámico \(una variable\) en la condición.|