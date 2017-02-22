---
title: "Advertencias sobre uso | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.usagerules"
helpviewer_keywords: 
  - "advertencias, uso"
  - "advertencias de análisis de código administrado, advertencias de uso"
  - "advertencias de uso"
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Advertencias sobre uso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de uso admiten el uso apropiado de .NET Framework.  
  
## En esta sección  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)|Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método.|  
|[CA1806: No omitir resultados del método](../code-quality/ca1806-do-not-ignore-method-results.md)|Se crea un nuevo objeto pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y esta nunca se utiliza, o un método COM o P\/Invoke devuelve un código de error o HRESULT que nunca se utiliza.|  
|[CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Un método que es una implementación de Dispose no llama a GC.SuppressFinalize, o un método que no es una implementación de Dispose llama a GC.SuppressFinalize, o un método llama a GC.SuppressFinalize y pasa algo distinto de "this" \(Me en Visual Basic\).|  
|[CA2200: Iniciar de nuevo para preservar los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Se vuelve a producir una excepción y se especifica explícitamente en la instrucción throw.  Si se vuelve a producir una excepción especificándola en la instrucción throw, se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual.|  
|[CA2201: No provocar tipos de excepción reservados](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Esto hace que el error original sea difícil de detectar y depurar.|  
|[CA2202: No aplicar Dispose a los objetos varias veces](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|La implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a System.IDisposable.Dispose o a un equivalente de Dispose \(como un método Close\(\) en algunos tipos\) en el mismo objeto.|  
|[CA2204: Debe escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Una cadena literal en el cuerpo de un método contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.|  
|[CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Se define un método de invocación de plataforma y hay un método con la funcionalidad equivalente en la biblioteca de clases de .NET Framework.|  
|[CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Un tipo de valor declara un constructor estático explícito.  Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.|  
|[CA2208: Crear instancias de las excepciones del argumento correctamente](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Se realiza una llamada al constructor predeterminado \(sin parámetros\) de un tipo de excepción que es o deriva de ArgumentException, o se pasa un argumento de cadena incorrecto a un constructor parametrizado de un tipo de excepción que es o deriva de ArgumentException.|  
|[CA2211: Los campos no constantes no deben ser visibles](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos.  Obtener acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase.|  
|[CA2212: No marcar los componentes con servicio como WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Un método en un tipo que hereda de System.EnterpriseServices.ServicedComponent está marcado con System.Web.Services.WebMethodAttribute.  Dado que un método ServicedComponent y WebMethodAttribute tienen comportamientos y requisitos conflictivos para el flujo de transacción y el contexto, el comportamiento del método es incorrecto en algunas situaciones.|  
|[CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Un tipo que implementa System.IDisposable declara campos que son de tipos que también implementan IDisposable.  El método Dispose del tipo declarativo no llama al método Dispose del campo.|  
|[CA2214: No llamar a métodos reemplazables en constructores](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor para la instancia que invoca el método.|  
|[CA2215: Los métodos Dispose deben llamar a Dispose de clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Si un tipo hereda de un tipo descartable, debe llamar al método Dispose del tipo base desde su propio método Dispose.|  
|[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Un tipo que implementa System.IDisposable y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador descrito por Object.Finalize.|  
|[CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Una enumeración visible externamente está marcada con FlagsAttribute y tiene uno o varios valores que no son potencias de dos o una combinación de los otros valores definidos en la enumeración.|  
|[CA2218: Reemplazar el método GetHashCode al reemplazar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode devuelve un valor basado en la instancia actual que es adecuado para los algoritmos hash y las estructuras de datos como una tabla hash.  Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash.|  
|[CA2219: No producir excepciones en cláusulas de excepción](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Cuando se genera una excepción en una cláusula finally o fault, la nueva excepción oculta la excepción activa.  Cuando se genera una excepción en una cláusula filter, el runtime la detecta automáticamente.  Esto hace que el error original sea difícil de detectar y depurar.|  
|[CA2220: Los finalizadores deben llamar al finalizador de la clase base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|La finalización se debe difundir a través de la jerarquía de herencia.  Para garantizar esto, los tipos deben llamar a su método Finalize de clase base en su propio método Finalize.|  
|[CA2221: Debe proteger los finalizadores](../code-quality/ca2221-finalizers-should-be-protected.md)|Los finalizadores deben utilizar el modificador de acceso de familia.|  
|[CA2222: No reducir la visibilidad del miembro heredado](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|No debería cambiar el modificador de acceso para los miembros heredados.  Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método.|  
|[CA2223: Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Aunque Common Language Runtime permite utilizar tipos de valor devuelto para diferenciar miembros idénticos, esta característica no se encuentra en Common Language Specification ni es una característica común de los lenguajes de programación de .NET.|  
|[CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Un tipo público implementa el operador de igualdad, pero no reemplaza Object.Equals.|  
|[CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado.  El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador; esto se hace para los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.|  
|[CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto.|  
|[CA2227: Las propiedades de la colección deben ser de solo lectura](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Una propiedad de colección grabable permite al usuario reemplazar la colección por otra diferente.  Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales.|  
|[CA2228: No enviar formatos de recursos no lanzados](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Las versiones admitidas de .NET Framework no podrían utilizar los archivos de recursos compilados con versiones preliminares de .NET Framework.|  
|[CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)|Para corregir una infracción de esta regla, implemente el constructor de serialización.  Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.|  
|[CA2230: Usar parámetros para argumentos de variable](../code-quality/ca2230-use-params-for-variable-arguments.md)|Un tipo público o protegido contiene un método público o protegido que utiliza la convención de llamada VarArgs en lugar de la palabra clave params.|  
|[CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Un tipo de valor reemplaza Object.Equals pero no implementa el operador de igualdad.|  
|[CA2232: Marcar puntos de entrada de Windows Forms con STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso.  Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente.|  
|[CA2233: Las operaciones no deben desbordarse](../code-quality/ca2233-operations-should-not-overflow.md)|Las operaciones aritméticas no deben realizarse sin validar primero los operandos para asegurarse de que el resultado de la operación no se encuentra fuera del intervalo de valores posible de los tipos de datos que se utilicen.|  
|[CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "URI", "urn", "URN", "url" o "URL".  El tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene un parámetro System.Uri.|  
|[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.|  
|[LCA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Para corregir una infracción de esta regla, llame al método de tipo base GetObjectData o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.|  
|[CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Para que los tipos sean reconocidos como serializables por Common Language Runtime, deben estar marcados con el atributo SerializableAttribute incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz ISerializable.|  
|[CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.|  
|[CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Un tipo tiene un campo que está marcado con el atributo System.Runtime.Serialization.OptionalFieldAttribute y el tipo no proporciona métodos de control de eventos de deserialización.|  
|[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)|Para corregir una infracción de esta regla, haga que el método GetObjectData sea visible y reemplazable, y asegúrese de que todos los campos de instancia se incluyan en el proceso de serialización o se marquen explícitamente con el atributo NonSerializedAttribute.|  
|[CA2241: Proporcionar argumentos correctos para los métodos de formato](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|El argumento format pasado a System.String.Format no contiene un elemento de formato que corresponda a cada argumento de objeto o viceversa.|  
|[CA2242: Prueba para NaN correcta](../code-quality/ca2242-test-for-nan-correctly.md)|Esta expresión prueba un valor respecto a Single.Nan o Double.Nan.  Utilice IsNan\(Single\) o Double.IsNan\(Double\) para probar el valor.|  
|[CA2243: Los literales de cadena de atributo se deben analizar correctamente](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.|