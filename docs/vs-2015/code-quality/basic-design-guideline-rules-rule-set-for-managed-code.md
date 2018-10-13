---
title: Configuración de reglas reglas de directrices de diseño básicas para código administrado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed0728eb0daa5c1ff0f322db42f66373181f3e23
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184722"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de directrices de diseño básicas para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el conjunto de reglas reglas de directrices de diseño básicas de Microsoft a centrar en hacer que el código sea más fácil de entender y utilizar. Debe incluir este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir procedimientos recomendados para el código que es fácil de mantener.  
  
 Las reglas de directrices de diseño básico incluye todas las reglas en el conjunto de reglas reglas mínimas recomendadas de Microsoft. Para obtener una lista de las reglas mínimas, consulte [pravidel administra reglas recomendadas para código administrado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 En la tabla siguiente se describe todas las reglas en el conjunto de reglas reglas de directrices de diseño básicas de Microsoft.  
  
|Regla|Descripción|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declare los controladores de evento correctamente|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marque los ensamblados con AssemblyVersionAttribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Los métodos de interfaz deben ser tipos secundarios|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Los tipos que poseen recursos nativos deben ser descartables|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mueva P/Invokes a la clase NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|No oculte métodos de clase base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implemente IDisposable correctamente|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|No producir excepciones en ubicaciones inesperadas|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Deben existir puntos de entrada P/Invoke|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke no deben estar visibles|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Tipos de diseño automático no deben ser visibles para COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Llame a GetLastError inmediatamente después de P/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Tipos bases de tipos visibles COM deben ser visibles para COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Métodos de registro COM se deben asociar|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declare los elementos P/Invoke correctamente|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar los finalizadores vacíos|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Campos de tipo de valor deberían ser portátiles|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Las declaraciones P/Invoke deben ser portátiles|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|No bloquear objetos con identidad débil|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revisar consultas SQL para las vulnerabilidades de seguridad|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique serialización para argumentos de cadena P/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revisar la seguridad declarativa en los tipos de valor|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Punteros no deberían estar visibles|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Los tipos seguros no deberían exponer campos|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Seguridad del método debe ser un supraconjunto del tipo|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|LOS métodos APTCA solo deben llamar a métodos APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Los tipos APTCA solo amplían tipos base APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|No exponer indirectamente métodos con peticiones de vínculo|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Las peticiones de vínculo deben ser idénticas de base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluir finally vulnerables externa cláusulas try|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Las peticiones de vínculo de tipos requieren peticiones de herencias|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Los tipos críticos de seguridad no pueden participar en la equivalencia de tipos|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Los constructores predeterminados deben ser al menos tan críticos como los constructores predeterminados de tipo base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Métodos transparentes deben contener solo IL que se pueda comprobar|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Los métodos transparentes no deben satisfacer LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Tipos deben ser al menos tan críticos como sus interfaces y tipos base|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Los métodos transparentes no pueden usar seguridad aserciones|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Los métodos transparentes no deben llamar a código nativo|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Reiniciar para mantener los detalles de la pila|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|No desechar objetos varias veces|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de valor insertados|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|No marcar los componentes con servicio como WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos desechables se deben desechar|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|No llame a métodos reemplazables en constructores|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Los tipos descartables deben declarar el finalizador|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Los finalizadores deben llamar al finalizador de la clase base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementar constructores de serialización|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Puntos de entrada de la marca Windows Forms con STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos los campos no serializables|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Llamar a métodos de clase base en tipos ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar los tipos ISerializable con SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar métodos de serialización correctamente|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementar ISerializable correctamente|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Proporcionar argumentos correctos a los métodos de formato|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Prueba para NaN correcta|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|No declarar a miembros estáticos en tipos genéricos|  
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|No exponer listas genéricas|  
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Utilizar instancias de controlador de eventos genéricos|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Métodos genéricos deben proporcionar un parámetro de tipo|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evite parámetros excesivos en tipos genéricos|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|No anidar tipos genéricos en firmas de miembro|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utilizar valores genéricos cuando sea apropiado|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Las enumeraciones deben tener el valor cero|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Las colecciones deben implementar la interfaz genérica|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Considere la posibilidad de pasar los tipos base como parámetros|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Tipos abstractos no deberían tener constructores|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Operador de sobrecarga es igual al sobrecargar la suma y resta|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marque los ensamblados con CLSCompliantAttribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marque los ensamblados con ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marcar atributos con AttributeUsageAttribute|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definir descriptores de acceso para los argumentos de atributo|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Los indizadores no deben ser multidimensionales|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utilizar las propiedades donde corresponda|  
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Reemplaza argumentos repetitivos con una matriz de parámetros|  
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|No se debería utilizar parámetros predeterminados|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marcar enumeraciones con FlagsAttribute|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Almacenamiento de enum debe ser Int32|  
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Utilizar eventos cuando sea apropiado|  
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|No capturar los tipos de excepción general|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementar constructores de excepción estándar|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Tipos anidados no deben ser visibles|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Las implementaciones de ICollection tienen miembros fuertemente tipados|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Invalidar métodos en tipos comparables|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Los enumeradores deben estar fuertemente tipados|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Las listas están fuertemente tipadas|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Proporcionar un mensaje ObsoleteAttribute|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utilizar argumento integral o de cadena para los indizadores|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Las propiedades no deberían ser de solo escritura|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|No sobrecargar el operador de igualdad en los tipos de referencia|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|No declarar miembros protegidos en tipos sealed|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|No declarar a miembros virtuales en tipos sealed|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Declarar tipos en espacios de nombres|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|No declarar campos de instancia visibles|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Los tipos titulares estáticos deben ser sealed|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Los tipos titulares estáticos no deben tener constructores|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Los parámetros de URI no deben ser cadenas|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI devuelven valores no deben ser cadenas|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Las propiedades URI no deben ser cadenas|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Tipos no deben ampliar ciertos tipos base|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Los miembros no deben exponer algunos tipos concretos|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Las excepciones deben ser públicas|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Los nombres de variable no deben coincidir con los nombres de campo|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evite la excesiva complejidad|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Los identificadores deben diferenciarse por algo más que el caso|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Los identificadores no deberían coincidir con palabras clave|  
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Revisar parámetros sin utilizar|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Quitar a variables locales no utilizadas|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Evitar a variables locales excesivas|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de referencia insertados|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Evitar código privado fuera de lugar|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Evitar las clases internas sin instancia|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Evitar atributos no sellados|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Preferir las matrices escalonadas antes que multidimensionales|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Invalidar equals y el operador equals en los tipos de valor|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Las propiedades no deberían devolver matrices|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Probar las cadenas están vacías mediante la longitud de cadena|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Marcar el miembro como estático|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Evitar los campos privados sin utilizar|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|No provocar tipos de excepción reservados|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilizar equivalentes administrados de la API Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Crear instancias de las excepciones del argumento correctamente|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Los campos no constantes no deben ser visibles|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|No marcar enumeraciones con FlagsAttribute|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|No producir excepciones en cláusulas de excepción|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Deben proteger los finalizadores|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|No disminuir la visibilidad del miembro heredado|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Los miembros deben diferenciarse por el tipo de valor devuelto más de|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Invalidar equals al sobrecargar operadores de igualdad|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Las sobrecargas del operador tienen alternativas con nombre|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Los operadores deben tener sobrecargar simétricas|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Propiedades de la colección deben ser de solo lectura|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Usar parámetros para argumentos de variable|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Pase objetos System.Uri en lugar de cadenas|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Proporcionar métodos de deserialización para campos opcionales|



