---
title: Configuración de reglas reglas de corrección básicas para código administrado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b435d813ad1e7c9308bfa6a7d8d243b877d6d6b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184598"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de corrección básicas para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El conjunto de reglas reglas de corrección básicas se centra en errores lógicos y errores comunes en el uso de las API del marco de trabajo. Las reglas de corrección básicas se incluyen las reglas en el conjunto de reglas reglas mínimas recomendadas. Para obtener más información, consulte [pravidel administra reglas recomendadas para código administrado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) debe incluir este conjunto de reglas para ampliar la lista de advertencias que las reglas mínimas recomendadas.  
  
 En la tabla siguiente se describe todas las reglas en el conjunto de reglas reglas de corrección básicas de Microsoft.  
  
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Las enumeraciones deben tener el valor cero|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Operador de sobrecarga es igual al sobrecargar la suma y resta|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|No pasar literales como parámetros localizados|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar las cadenas a mayúsculas|  
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|No omitir resultados del método|  
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Llamar a GC. SuppressFinalize correctamente|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Las propiedades no deberían devolver matrices|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Probar las cadenas están vacías mediante la longitud de cadena|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Usar solo API de .NET framework de destino|  
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Quite las llamadas a GC. KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Utilizar SafeHandle para encapsular recursos nativos|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|No declarar tipos de referencias mutables de solo lectura|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Campos de matriz deben no ser de solo lectura|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Asegurar aserciones|  
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Llamar a GC. KeepAlive cuando se utilicen recursos nativos|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Sellar los métodos que satisfacen las interfaces privadas|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Proteger los constructores de serialización|  
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Los constructores estáticos deberían ser privados|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Las constantes críticas de seguridad deben ser transparentes|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilizar equivalentes administrados de la API Win32|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Los métodos Dispose deben llamar al método dispose de clase base|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Deben proteger los finalizadores|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|No disminuir la visibilidad del miembro heredado|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Los miembros deben diferenciarse por el tipo de valor devuelto más de|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Invalidar equals al sobrecargar operadores de igualdad|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Los operadores deben tener sobrecargar simétricas|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Propiedades de la colección deben ser de solo lectura|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Proporcionar métodos de deserialización para campos opcionales|



