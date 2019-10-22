---
title: advertencias de uso
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 423367381c9b4624b9b3f4f739b017231276c76d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649067"
---
# <a name="usage-warnings"></a>advertencias de uso

Las advertencias de uso admiten el uso correcto de .NET.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801.md)|Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método.|
|[CA1806: No omitir resultados del método](../code-quality/ca1806.md)|Se crea un nuevo objeto pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y esta nunca se utiliza, o un método COM o P/Invoke devuelve un código de error o HRESULT que nunca se utiliza.|
|[CA1816: Llame a GC.SuppressFinalize correctamente](../code-quality/ca1816.md)|Un método que es una implementación de Dispose no llama a GC. SuppressFinalize o un método que no es una implementación de Dispose llama a GC. SuppressFinalize o un método llama a GC. SuppressFinalize y pasa algo distinto de This (me en Visual Basic).|
|[CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200.md)|Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw. Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual.|
|[CA2201: No provocar tipos de excepción reservados](../code-quality/ca2201.md)|Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2202: No usar Dispose varias veces en objetos](../code-quality/ca2202.md)|La implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a System.IDisposable.Dispose o a un equivalente de Dispose (como un método Close() en algunos tipos) en el mismo objeto.|
|[CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204.md)|Una cadena literal en el cuerpo de un método contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|
|[CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205.md)|Se define un método de invocación de plataforma y hay disponible un método .NET con la funcionalidad equivalente.|
|[CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207.md)|Un tipo de valor declara un constructor estático explícito. Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.|
|[CA2208: Crear instancias de las excepciones del argumento correctamente](../code-quality/ca2208.md)|Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de ArgumentException.|
|[CA2211: Los campos no constantes no deben ser visibles](../code-quality/ca2211.md)|Los campos estáticos que no son constantes o de solo lectura no son seguros para subprocesos. El acceso a este tipo de campo debe controlarse cuidadosamente y requiere técnicas de programación avanzada para sincronizar el acceso al objeto de clase.|
|[CA2212: No marcar los componentes con servicio como WebMethod](../code-quality/ca2212.md)|Un método de un tipo que hereda de System. EnterpriseServices. ServicedComponent se marca con System. Web. Services. WebMethodAttribute. Dado que un método ServicedComponent y WebMethodAttribute tienen comportamientos y requisitos conflictivos para el flujo de transacción y el contexto, el comportamiento del método es incorrecto en algunas situaciones.|
|[CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213.md)|Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable. El método Dispose del tipo declarativo no llama al método Dispose del campo.|
|[CA2214: No llamar a métodos reemplazables en constructores](../code-quality/ca2214.md)|Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor de la instancia que invoca el método.|
|[CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215.md)|Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose.|
|[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216.md)|Un tipo que implementa System. IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal y como se describe en Object. Finalize.|
|[CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217.md)|Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o más valores que no son potencias de dos o una combinación de los demás valores definidos en la enumeración.|
|[CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218.md)|GetHashCode devuelve un valor basado en la instancia actual que es adecuado para los algoritmos hash y las estructuras de datos como una tabla hash. Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash.|
|[CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219.md)|Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa. Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente. Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2220: Los finalizadores deben llamar al finalizador de la clase base](../code-quality/ca2220.md)|La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su método Finalize de clase base en su propio método Finalize.|
|[CA2221: Debe proteger los finalizadores](../code-quality/ca2221.md)|Los finalizadores deben utilizar el modificador de acceso de familia.|
|[CA2222: No disminuir la visibilidad del miembro heredado](../code-quality/ca2222.md)|No cambie el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método.|
|[CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto](../code-quality/ca2223.md)|Aunque Common Language Runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no se encuentra en Common Language Specification ni es una característica común de los lenguajes de programación de .NET.|
|[CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224.md)|Un tipo público implementa el operador de igualdad, pero no invalida Object. Equals.|
|[CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225.md)|Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador y se proporciona a los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.|
|[CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226.md)|Un tipo implementa el operador de igualdad o desigualdad y no implementa el operador opuesto.|
|[CA2227: Las propiedades de la colección deben ser de solo lectura](../code-quality/ca2227.md)|Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales.|
|[CA2228: No enviar formatos de recursos no lanzados](../code-quality/ca2228.md)|Los archivos de recursos que se compilaron con versiones preliminares de .NET podrían no ser utilizados por las versiones compatibles de .NET.|
|[CA2229: Implementar constructores de serialización](../code-quality/ca2229.md)|Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.|
|[CA2230: Usar parámetros para argumentos de variable](../code-quality/ca2230.md)|Un tipo público o protegido contiene un método público o protegido que utiliza la convención de llamada VarArgs en lugar de la palabra clave params.|
|[CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231.md)|Un tipo de valor invalida `Object.Equals` pero no implementa el operador de igualdad.|
|[CA2232: Marcar puntos de entrada de Windows Forms con STAThread](../code-quality/ca2232.md)|STAThreadAttribute indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente.|
|[CA2233: Las operaciones no deben desbordarse](../code-quality/ca2233.md)|No se deben realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados.|
|[CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234.md)|Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL".  El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri.|
|[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235.md)|Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.|
|[CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236.md)|Para corregir una infracción de esta regla, llame al método de tipo base GetObjectData o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.|
|[CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237.md)|Para ser reconocibles por el Common Language Runtime como serializable, los tipos se deben marcar con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable.|
|[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238.md)|Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.|
|[CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239.md)|Un tipo tiene un campo que se marca con el atributo System. Runtime. Serialization. OptionalFieldAttribute y el tipo no proporciona métodos de control de eventos de deserialización.|
|[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240.md)|Para corregir una infracción de esta regla, haga que el método GetObjectData sea visible y Overridable, y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o que se marcan explícitamente con el atributo NonSerializedAttribute.|
|[CA2241: Proporcionar argumentos correctos a los métodos de formato](../code-quality/ca2241.md)|El argumento de formato pasado a System. String. Format no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.|
|[CA2242: Prueba para NaN correcta](../code-quality/ca2242.md)|Esta expresión prueba un valor respecto a Single.Nan o Double.Nan. Utilice IsNan(Single) o Double.IsNan(Double) para probar el valor.|
|[CA2243: Los literales de cadena de atributo se deben analizar correctamente](../code-quality/ca2243.md)|El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.|
