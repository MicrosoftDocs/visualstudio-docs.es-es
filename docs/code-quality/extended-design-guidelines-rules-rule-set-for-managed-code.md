---
title: Conjunto de reglas Reglas de directrices de diseño ampliadas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e54a031e69957579974e67af124b0e88a0d95abb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816616"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de directrices de diseño ampliadas para código administrado
El conjunto de reglas reglas de directrices de diseño extendidas de Microsoft se expande en las reglas de directrices de diseño básicas para maximizar los problemas de facilidad de uso y mantenimiento que se notifican. Se pone especial énfasis en las directrices de nomenclatura. Considere incluir este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir los más altos estándares para escribir código fácil de mantener.

 Las reglas de directrices de diseño extendidas incluyen todas las reglas de directrices de diseño básicas de Microsoft. Las reglas de directrices de diseño básico incluye todas las reglas mínimas recomendadas de Microsoft. Para obtener más información, consulte [de conjunto de reglas de reglas de directrices de diseño básicas para código administrado](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) y [pravidel administra reglas recomendadas para código administrado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 En la tabla siguiente se describe todas las reglas en el conjunto de reglas reglas de directrices de diseño extendidas de Microsoft.

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
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar finalizadores vacíos|
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
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Reiniciar para mantener los detalles de la pila|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|No usar Dispose varias veces en objetos|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos descartables deben ser descartables|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|No llamar a métodos reemplazables en constructores|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementar constructores de serialización|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementar ISerializable correctamente|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Comprobar NaN correctamente|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|No declarar miembros estáticos en tipos genéricos|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|No exponer listas genéricas|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Utilizar instancias genéricas de controlador de eventos|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Los métodos genéricos deben proporcionar un parámetro de tipo|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evitar los parámetros excesivos en tipos genéricos|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|No anidar tipos genéricos en signaturas de miembro|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utilizar valores genéricos cuando sea posible|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Las enumeraciones deben tener un valor igual a cero|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Las colecciones deben implementar la interfaz genérica|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Considerar pasar los tipos base como parámetros|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Los tipos abstractos no deberían tener constructores|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marcar los ensamblados con CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marcar los ensamblados con ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marcar atributos con AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definir descriptores de acceso para los argumentos de atributo|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Los indizadores no deben ser multidimensionales|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utilizar las propiedades donde corresponda|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Reemplazar argumentos repetitivos por una matriz de parámetros|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|No deben usarse parámetros predeterminados|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marcar enumeraciones con FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|El almacenamiento de la enumeración debe ser de tipo Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Utilizar eventos cuando sea apropiado|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|No capturar los tipos de excepción general|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar constructores de excepción estándar|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Los tipos anidados no deben ser visibles|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Las implementaciones de ICollection tienen miembros fuertemente tipados|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Invalidar métodos en tipos comparables|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Los enumeradores deben estar fuertemente tipados|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Las listas están fuertemente tipadas|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Proporcionar un mensaje ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utilizar un argumento integral o de cadena en indizadores|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Las propiedades no deben ser de solo escritura|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|No sobrecargar el operador de igualdad en los tipos de referencia|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|No declarar miembros protegidos en tipos sellados|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|No declarar miembros virtuales en tipos sellados|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Declarar tipos en espacios de nombres|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|No declarar campos de instancia visibles|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Los tipos titulares estáticos deben estar sellados|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Los tipos titulares estáticos no deben tener constructores|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Los parámetros de URI no deben ser cadenas|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Los valores devueltos URI no deben ser cadenas|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Las propiedades URI no deben ser cadenas|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Los tipos no deben ampliar ciertos tipos base|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Los miembros no deben exponer algunos tipos concretos|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Las excepciones deben ser públicas|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Los nombres de las variables no deben coincidir con los nombres de los campos|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evitar una complejidad excesiva|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Los identificadores no deben coincidir con palabras clave|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Revisar parámetros sin utilizar|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Quitar variables locales no utilizadas|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Evitar las variables locales excesivas|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de referencia insertados|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Evitar código privado al que no se llama|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Evitar las clases internas sin instancia|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Evitar los atributos no sellados|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Preferir matrices escalonadas antes que multidimensionales|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Invalidar Equals y el operador Equals en los tipos de valores|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Las propiedades no deben devolver matrices|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Marcar miembros como estáticos|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Evitar los campos privados sin utilizar|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|No provocar tipos de excepción reservados|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Crear instancias de las excepciones del argumento correctamente|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Los campos no constantes no deben ser visibles|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|No marcar enumeraciones con FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|No producir excepciones en cláusulas de excepción|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Las sobrecargas del operador tienen alternativas con nombre|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Las propiedades de la colección deben ser de solo lectura|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Usar parámetros en argumentos de variable|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Pasar objetos System.Uri en lugar de cadenas|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Proporcionar métodos de deserialización para campos opcionales|
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Evitar los espacios de nombres con pocos tipos|
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Evitar los parámetros out|
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Evitar las interfaces vacías|
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|No pasar tipos por referencia|
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Validar argumentos de métodos públicos|
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Evitar una herencia excesiva|
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Revisar los nombres de campos erróneos|
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Evitar código que no se puede mantener|
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Evitar el acoplamiento excesivo de clases|
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|No nombrar valores de enumeración como 'Reserved'|
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente|
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente|
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|La ortografía de las cadenas de recursos debe ser correcta|
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|La ortografía de los identificadores debe ser correcta|
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Los identificadores no deben contener caracteres de subrayado|
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Los identificadores deben utilizar las mayúsculas y minúsculas correctamente|
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Los identificadores deben tener un sufijo correcto|
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Los identificadores no deben tener un sufijo incorrecto|
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|No utilizar prefijos en valores de enumeración con el nombre del tipo|
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Los eventos no deben tener prefijos antes ni después|
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Las enumeraciones Flags deben tener nombres en plural|
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Los identificadores deben tener el prefijo correcto|
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Solo las enumeraciones FlagsAttribute deben tener nombres en plural|
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Los nombres de parámetro no deben coincidir con los nombres de miembro|
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Los identificadores no deben contener nombres de tipo|
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Los nombres de propiedades no deben coincidir con los métodos get|
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Los identificadores no deben tener un prefijo incorrecto|
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Los nombres de tipo no deben coincidir con los espacios de nombres|
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Los nombres de parámetro deben coincidir con la declaración base|
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Utilizar términos preferidos|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Los literales deben estar escritos correctamente|