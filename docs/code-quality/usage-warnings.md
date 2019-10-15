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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305687"
---
# <a name="usage-warnings"></a>advertencias de uso

Las advertencias de uso admiten el uso correcto de .NET.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1801: Revisar los parámetros no usados @ no__t-0|Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método.|
|[CA1806: No pasar por alto los resultados del método @ no__t-0|Se crea un nuevo objeto pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y esta nunca se utiliza, o un método COM o P/Invoke devuelve un código de error o HRESULT que nunca se utiliza.|
|[CA1816: Llame a GC. SuppressFinalize correctamente @ no__t-0|Un método que es una implementación de Dispose no llama a GC. SuppressFinalize; o un método que no es una implementación de Dispose llama a GC. SuppressFinalize; o un método llama a GC. SuppressFinalize y pasa un valor distinto de esto (Me en Visual Basic).|
|[CA2200: Volver a iniciar para conservar los detalles de la pila @ no__t-0|Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw. Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual.|
|@NO__T 0CA2201: No generar tipos de excepción reservados @ no__t-0|Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2202: No eliminar objetos varias veces @ no__t-0|La implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a System.IDisposable.Dispose o a un equivalente de Dispose (como un método Close() en algunos tipos) en el mismo objeto.|
|[CA2204: Los literales deben estar escritos correctamente @ no__t-0|Una cadena literal en el cuerpo de un método contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|
|[CA2205: Usar equivalentes administrados de la API Win32 @ no__t-0|Se define un método de invocación de plataforma y hay disponible un método .NET con la funcionalidad equivalente.|
|@NO__T 0CA2207: Inicializar campos estáticos de tipo de valor en línea @ no__t-0|Un tipo de valor declara un constructor estático explícito. Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.|
|[CA2208: Cree instancias de las excepciones de argumento correctamente @ no__t-0|Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de ArgumentException.|
|@NO__T 0CA2211: Los campos no constantes no deben ser visibles @ no__t-0|Los campos estáticos que no son constantes o de solo lectura no son seguros para subprocesos. El acceso a este tipo de campo debe controlarse cuidadosamente y requiere técnicas de programación avanzada para sincronizar el acceso al objeto de clase.|
|[CA2212: No marcar los componentes con servicio con WebMethod @ no__t-0|Un método de un tipo que hereda de System. EnterpriseServices. ServicedComponent se marca con System. Web. Services. WebMethodAttribute. Dado que un método ServicedComponent y WebMethodAttribute tienen comportamientos y requisitos conflictivos para el flujo de transacción y el contexto, el comportamiento del método es incorrecto en algunas situaciones.|
|[CA2213: los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable. El método Dispose del tipo declarativo no llama al método Dispose del campo.|
|@NO__T 0CA2214: No llamar a métodos reemplazables en constructores @ no__t-0|Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor de la instancia que invoca el método.|
|@NO__T 0CA2215: Los métodos Dispose deben llamar a la clase base Dispose @ no__t-0|Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose.|
|[CA2216: Los tipos descartables deben declarar el finalizador @ no__t-0|Un tipo que implementa System. IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal y como se describe en Object. Finalize.|
|@NO__T 0CA2217: No marcar enumeraciones con FlagsAttribute @ no__t-0|Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o más valores que no son potencias de dos o una combinación de los demás valores definidos en la enumeración.|
|[CA2218: Invalide GetHashCode al reemplazar Equals @ no__t-0|GetHashCode devuelve un valor basado en la instancia actual que es adecuado para los algoritmos hash y las estructuras de datos como una tabla hash. Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash.|
|@NO__T 0CA2219: No producir excepciones en cláusulas de excepción @ no__t-0|Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa. Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente. Esto hace que el error original sea difícil de detectar y depurar.|
|[CA2220: Los finalizadores deben llamar al finalizador de la clase base @ no__t-0|La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su método Finalize de clase base en su propio método Finalize.|
|[CA2221: Los finalizadores deben estar protegidos @ no__t-0|Los finalizadores deben utilizar el modificador de acceso de familia.|
|[CA2222: No disminuir la visibilidad de los miembros heredados @ no__t-0|No cambie el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método.|
|[CA2223: Los miembros deben diferenciarse por algo más que el tipo de valor devuelto @ no__t-0|Aunque Common Language Runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no se encuentra en Common Language Specification ni es una característica común de los lenguajes de programación de .NET.|
|@NO__T 0CA2224: Reemplazar Equals en el operador de sobrecarga es igual a @ no__t-0|Un tipo público implementa el operador de igualdad, pero no invalida Object. Equals.|
|@NO__T 0CA2225: Las sobrecargas de operador tienen alternativas con nombre @ no__t-0|Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador y se proporciona a los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.|
|[CA2226: Los operadores deben tener sobrecargas simétricas @ no__t-0|Un tipo implementa el operador de igualdad o desigualdad y no implementa el operador opuesto.|
|[CA2227: Las propiedades de la colección deben ser de solo lectura @ no__t-0|Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales.|
|[CA2228: No enviar formatos de recursos no lanzados @ no__t-0|Los archivos de recursos que se compilaron con versiones preliminares de .NET podrían no ser utilizados por las versiones compatibles de .NET.|
|[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)|Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.|
|[CA2230: Usar parámetros para argumentos de variable @ no__t-0|Un tipo público o protegido contiene un método público o protegido que utiliza la convención de llamada VarArgs en lugar de la palabra clave params.|
|[CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un tipo de valor invalida `Object.Equals` pero no implementa el operador de igualdad.|
|[CA2232: Marcar Windows Forms puntos de entrada con STAThread @ no__t-0|STAThreadAttribute indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente.|
|[CA2233: Las operaciones no deben desbordarse @ no__t-0|No se deben realizar operaciones aritméticas sin validar primero los operandos para asegurarse de que el resultado de la operación no está fuera del intervalo de valores posibles para los tipos de datos implicados.|
|[CA2234: Pasar objetos System. Uri en lugar de cadenas @ no__t-0|Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL".  El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri.|
|[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.|
|[CA2236: Llamar a métodos de clase base en tipos ISerializable @ no__t-0|Para corregir una infracción de esta regla, llame al método de tipo base GetObjectData o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.|
|[CA2237: Marcar tipos ISerializable con SerializableAttribute @ no__t-0|Para ser reconocibles por el Common Language Runtime como serializable, los tipos se deben marcar con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable.|
|[CA2238: Implementar métodos de serialización correctamente @ no__t-0|Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.|
|@NO__T 0CA2239: Proporcionar métodos de deserialización para campos opcionales @ no__t-0|Un tipo tiene un campo que se marca con el atributo System. Runtime. Serialization. OptionalFieldAttribute y el tipo no proporciona métodos de control de eventos de deserialización.|
|[CA2240: Implementar ISerializable correctamente @ no__t-0|Para corregir una infracción de esta regla, haga que el método GetObjectData sea visible y Overridable, y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o que se marcan explícitamente con el atributo NonSerializedAttribute.|
|[CA2241: Proporcione los argumentos correctos para los métodos de formato @ no__t-0|El argumento de formato pasado a System. String. Format no contiene un elemento de formato que corresponda a cada argumento de objeto, o viceversa.|
|[CA2242: Prueba para NaN correctamente @ no__t-0|Esta expresión prueba un valor respecto a Single.Nan o Double.Nan. Utilice IsNan(Single) o Double.IsNan(Double) para probar el valor.|
|[CA2243: Los literales de cadena de atributo se deben analizar correctamente @ no__t-0|El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.|