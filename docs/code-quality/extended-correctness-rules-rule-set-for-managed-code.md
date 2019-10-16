---
title: Conjunto de reglas Reglas de corrección extendidas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 96a0b43e6d300d3db425cb7a926d0196566d178b
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349636"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de corrección extendidas para código administrado

El conjunto de reglas reglas de corrección extendidas de Microsoft maximiza los errores de uso de la lógica y el marco de trabajo que se indican en el análisis de código. Se pone especial énfasis en escenarios específicos como la interoperabilidad COM y las aplicaciones móviles. Debe considerar la posibilidad de incluir este conjunto de reglas si alguno de estos escenarios se aplica a su proyecto o para buscar problemas adicionales en el proyecto.

El conjunto de reglas reglas de corrección extendidas de Microsoft incluye las reglas que se encuentran en el conjunto de reglas [reglas de corrección básicas](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , que contiene las reglas que se encuentran en el conjunto de reglas [reglas recomendadas administradas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

En la tabla siguiente se describen todas las reglas del conjunto de reglas reglas de corrección extendidas de Microsoft.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declarar los controladores de evento correctamente|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|No ocultar métodos de clase base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementar IDisposable correctamente|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declarar elementos P/Invoke correctamente|
|[CA1821](../code-quality/ca1821.md)|Quitar finalizadores vacíos|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Los campos de tipo de valor deben ser portátiles|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Las declaraciones P/Invoke deben ser portátiles|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|No bloquear objetos con identidad débil|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar serialización en argumentos de cadena P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|No exponer indirectamente métodos con peticiones de vínculos|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Las peticiones de vínculos de invalidaciones deben ser idénticas a la base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluir cláusulas finally vulnerables en un bloque try externo|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Los métodos deben mantener una transparencia coherente al invalidar métodos base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Los métodos transparentes deben contener solo IL que se pueda comprobar|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Los métodos transparentes no deben satisfacer LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Los métodos transparentes no pueden usar aserciones de seguridad|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Los métodos transparentes no deben llamar a código nativo|
|[CA2200](../code-quality/ca2200.md)|Reiniciar para mantener los detalles de la pila|
|[CA2202](../code-quality/ca2202.md)|No usar Dispose varias veces en objetos|
|[CA2207](../code-quality/ca2207.md)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](../code-quality/ca2213.md)|Los campos descartables deben ser descartables|
|[CA2214](../code-quality/ca2214.md)|No llamar a métodos reemplazables en constructores|
|[CA2216](../code-quality/ca2216.md)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](../code-quality/ca2229.md)|Implementar constructores de serialización|
|[CA2231](../code-quality/ca2231.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](../code-quality/ca2235.md)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable correctamente|
|[CA2241](../code-quality/ca2241.md)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](../code-quality/ca2242.md)|Comprobar NaN correctamente|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Las enumeraciones deben tener un valor igual a cero|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|No pasar literales como parámetros localizados|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar cadenas en mayúsculas|
|[CA1806](../code-quality/ca1806.md)|No omitir resultados del método|
|[CA1816](../code-quality/ca1816.md)|Llamar a GC.SuppressFinalize correctamente|
|[CA1819](../code-quality/ca1819.md)|Las propiedades no deben devolver matrices|
|[CA1820](../code-quality/ca1820.md)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Usar solo API de la versión de .NET Framework de destino|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Quitar las llamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Utilizar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Los campos de matrices no deben ser de solo lectura|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Proteger las aserciones|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Sellar los métodos que satisfacen las interfaces privadas|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Proteger los constructores de serializaciones|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Los constructores estáticos deben ser privados|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Las constantes críticas para la seguridad deben ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2215](../code-quality/ca2215.md)|Los métodos Dispose deben llamar al método Dispose de la clase base|
|[CA2221](../code-quality/ca2221.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2226](../code-quality/ca2226.md)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Las propiedades de la colección deben ser de solo lectura|
|[CA2239](../code-quality/ca2239.md)|Proporcionar métodos de deserialización para campos opcionales|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar constructores de excepción estándar|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Los parámetros de URI no deben ser cadenas|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Los valores devueltos URI no deben ser cadenas|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Las propiedades URI no deben ser cadenas|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Evitar las sobrecargas en interfaces visibles a través de COM|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Evitar los argumentos Int64 en clientes Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Evitar los miembros estáticos en tipos visibles a través de COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|No utilizar AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Los tipos visibles a través de COM se deben poder crear|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Los métodos de registro COM no deben ser visibles|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Marcar las interfaces ComSource como IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Evitar los campos no públicos en tipos de valor visibles a través de COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Marcar los argumentos P/Invoke booleanos con MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|No utilizar la prioridad del proceso inactiva|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|No utilizar temporizadores que impidan los cambios de estado de energía|
|[CA1824](../code-quality/ca1824.md)|Marcar los ensamblados con NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Evitar llamar a métodos problemáticos|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|No tratar fibras como subprocesos|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Los ensamblados de nivel 2 no deben contener LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Los miembros no deben tener anotaciones de transparencia en conflicto|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|El código transparente no debe protegerse con LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Los métodos transparentes no deben usar peticiones de seguridad|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|El código transparente no debe cargar ensamblados desde matrices de bytes|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Los literales deben estar escritos correctamente|
|[CA2211](../code-quality/ca2211.md)|Los campos no constantes no deben ser visibles|
|[CA2217](../code-quality/ca2217.md)|No marcar enumeraciones con FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Invalidar el método GetHashCode al invalidar el método Equals|
|[CA2219](../code-quality/ca2219.md)|No producir excepciones en cláusulas de excepción|
|[CA2225](../code-quality/ca2225.md)|Las sobrecargas del operador tienen alternativas con nombre|
|[CA2228](../code-quality/ca2228.md)|No enviar formatos de recursos no lanzados|
|[CA2230](../code-quality/ca2230.md)|Usar parámetros en argumentos de variable|
|[CA2233](../code-quality/ca2233.md)|Las operaciones no deben desbordarse|
|[CA2234](../code-quality/ca2234.md)|Pasar objetos System.Uri en lugar de cadenas|
|[CA2243](../code-quality/ca2243.md)|Los literales de cadena de atributo se deben analizar correctamente|