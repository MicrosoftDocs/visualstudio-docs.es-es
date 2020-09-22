---
title: Reglas de uso
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45dd58978bb37dd66023d8a28b9babf017bec262
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90806192"
---
# <a name="usage-rules"></a>Reglas de uso

Las reglas de uso admiten el uso adecuado de .NET.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801.md)|Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método.|
|[CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816.md)|Un método que es una implementación de Dispose no llama a GC.SuppressFinalize, o un método que no es una implementación de Dispose llama a GC.SuppressFinalize, o un método llama a GC.SuppressFinalize y pasa algo distinto de "this" (Me en Visual Basic).|
|[CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200.md)|Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw. Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual.|
|[CA2201: No provocar tipos de excepción reservados](../code-quality/ca2201.md)|Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2202: No usar Dispose varias veces en objetos](../code-quality/ca2202.md)|La implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a System.IDisposable.Dispose o a un equivalente de Dispose (como un método Close() en algunos tipos) en el mismo objeto.|
|[CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207.md)|Un tipo de valor declara un constructor estático explícito. Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.|
|[CA2208: Crear instancias de las excepciones del argumento correctamente](../code-quality/ca2208.md)|Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de ArgumentException.|
|[CA2211: Los campos no constantes no deben ser visibles](../code-quality/ca2211.md)|Los campos estáticos que no son constantes o de solo lectura no son seguros para subprocesos. El acceso a este tipo de campo debe controlarse cuidadosamente y requiere técnicas de programación avanzada para sincronizar el acceso al objeto de clase.|
|[CA2213: Los campos descartables deben ser descartables](../code-quality/ca2213.md)|Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable. El método Dispose del tipo declarativo no llama al método Dispose del campo.|
|[CA2214: No llamar a métodos reemplazables en constructores](../code-quality/ca2214.md)|Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor de la instancia que invoca el método.|
|[CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215.md)|Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose.|
|[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216.md)|Un tipo que implementa System. IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal y como se describe en Object. Finalize.|
|[CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217.md)|Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o más valores que no son potencias de dos o una combinación de los demás valores definidos en la enumeración.|
|[CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219.md)|Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa. Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente. Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225.md)|Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador y se proporciona a los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.|
|[CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226.md)|Un tipo implementa el operador de igualdad o desigualdad y no implementa el operador opuesto.|
|[CA2227: Las propiedades de la colección deben ser de solo lectura](../code-quality/ca2227.md)|Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales.|
|[CA2229: Implementar constructores de serialización](../code-quality/ca2229.md)|Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.|
|[CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231.md)|Un tipo de valor invalida `Object.Equals` pero no implementa el operador de igualdad.|
|[CA2232: Marcar puntos de entrada de Windows Forms con STAThread](../code-quality/ca2232.md)|STAThreadAttribute indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente.|
|[CA2233: Las operaciones no deben desbordarse](../code-quality/ca2233.md)|No se deben realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados.|
|[CA2234: Pasar objetos System.Uri en lugar de cadenas](../code-quality/ca2234.md)|Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL".  El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri.|
|[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235.md)|Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.|
|[CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236.md)|Para corregir una infracción de esta regla, llame al método de tipo base GetObjectData o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.|
|[CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237.md)|Para ser reconocibles por el Common Language Runtime como serializable, los tipos se deben marcar con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable.|
|[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238.md)|Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.|
|[CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239.md)|Un tipo tiene un campo que se marca con el atributo System. Runtime. Serialization. OptionalFieldAttribute y el tipo no proporciona métodos de control de eventos de deserialización.|
|[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240.md)|Para corregir una infracción de esta regla, haga que el método GetObjectData sea visible y Overridable, y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o que se marcan explícitamente con el atributo NonSerializedAttribute.|
|[CA2241: Proporcionar argumentos correctos a los métodos de formato](../code-quality/ca2241.md)|El argumento de formato pasado a System. String. Format no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.|
|[CA2242: Comprobar NaN correctamente](../code-quality/ca2242.md)|Esta expresión prueba un valor respecto a Single.Nan o Double.Nan. Utilice IsNan(Single) o Double.IsNan(Double) para probar el valor.|
|[CA2243: Los literales de cadena de atributo se deben analizar correctamente](../code-quality/ca2243.md)|El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.|
|[CA2244: No duplicar inicializaciones de elementos indexados](../code-quality/ca2244.md)|Un inicializador de objeto tiene más de un inicializador de elemento indizado con el mismo índice de constante. Todo menos el último inicializador son redundantes.|
|[CA2245: No asignar una propiedad a sí misma](../code-quality/ca2245.md)|Una propiedad se asignó accidentalmente a sí misma.|
|[CA2246: No asignar un símbolo y su miembro en la misma instrucción](../code-quality/ca2246.md)|No se recomienda asignar un símbolo y su miembro, es decir, un campo o una propiedad, en la misma instrucción. No está claro si el acceso a miembros debía usar el valor anterior del símbolo antes de la asignación o el nuevo valor de la asignación en esta instrucción.|
|[CA2247: El argumento pasado al constructor TaskCompletionSource debe ser una enumeración TaskCreationOptions en lugar de TaskContinuationOptions](../code-quality/ca2246.md)|TaskCompletionSource tiene constructores que toman un TaskCreationOptions que controla la tarea subyacente y constructores que toman el estado del objeto almacenado en la tarea.  Pasar accidentalmente un TaskContinuationOptions en lugar de un TaskCreationOptions dará lugar a que la llamada trate las opciones como estado.|
|[CA2248: proporcione el argumento ' ENUM ' correcto a ' enum. HasFlag '](../code-quality/ca2248.md)|El tipo de enumeración que se pasa como argumento a la `HasFlag` llamada al método es diferente del tipo de enumeración que realiza la llamada.|
|[CA2249: Valorar la posibilidad de usar String.Contains en lugar de String.IndexOf](../code-quality/ca2249.md)|Las llamadas a `string.IndexOf` donde se utiliza el resultado para comprobar la presencia o la ausencia de una subcadena se pueden reemplazar por `string.Contains` .|
