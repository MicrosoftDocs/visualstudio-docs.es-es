---
title: Conjunto de reglas Reglas de seguridad para código administrado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925047"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de seguridad para código administrado
Debe incluir el conjunto para maximizar el número de posibles problemas de seguridad que se notifican de reglas reglas de seguridad de Microsoft.

|Regla|Descripción|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revisar las consultas SQL en busca de vulnerabilidades de seguridad|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Revisar la seguridad imperativa|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Campos de matriz deben no ser de solo lectura|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Asegurar aserciones|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Revisión de deny y PermitOnly solo uso|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revisar la seguridad declarativa en los tipos de valor|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Revisar los controladores de eventos visibles|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Punteros no deberían estar visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Los tipos seguros no deberían exponer campos|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Seguridad del método debería ser un supraconjunto del tipo|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Llamar a GC. KeepAlive cuando se utilicen recursos nativos|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Los métodos APTCA solo deben llamar a métodos APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Revisar el uso de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Sellar los métodos que cumplan las interfaces privadas|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Proteger los constructores de serialización|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Constructores estáticos deberían ser privados|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|No exponer indirectamente métodos con peticiones de vínculo|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Las peticiones de vínculo de invalidación deben ser idénticas de base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluir finally vulnerables cláusulas en externa try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Las constantes críticas de seguridad deberían ser transparentes|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Los tipos críticos de seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Constructores predeterminados deben ser al menos tan críticos como constructores predeterminados del tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Métodos deben mantener una transparencia coherente cuando reemplazan métodos base|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Ensamblados de nivel 2 no deberían contener LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Los miembros no deben tener anotaciones de transparencia en conflicto|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Métodos transparentes deben contener solo IL comprobable|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Métodos transparentes no deben satisfacer LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|El código transparente no se debería proteger con LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Métodos transparentes no deben usar peticiones de seguridad|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|El código transparente no debe cargar ensamblados desde matrices de bytes|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Tipos deben ser al menos tan críticos como sus tipos base e interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Métodos transparentes no pueden usar seguridad aserciones|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Métodos transparentes no deben llamar a código nativo|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Los ensamblados deben tener nombres seguros válidos|