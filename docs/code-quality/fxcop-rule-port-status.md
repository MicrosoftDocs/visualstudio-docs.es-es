---
title: Estado del puerto de regla de FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0d78e7dcd7dfd203a15510037b277b8c2633805e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038651"
---
# <a name="fxcop-rule-port-status"></a>Estado del puerto de regla de FxCop

Si anteriormente ha usado el análisis de código estático en una versión anterior de Visual Studio, quizás se pregunte cuál de esas reglas están disponibles en la implementación actual como [analizadores de FxCop](install-fxcop-analyzers.md). Esta página enumera las reglas que se transfieren, así como los que aún no se ha trasladado y determinar si hay planes para migrarlas.

## <a name="ported-rules"></a>Reglas de portada

El [página de documentación generado automáticamente](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) en los analizadores de roslyn repositorio tiene la lista más actualizada de las reglas que se han trasladado a los analizadores de FxCop. Esa página también tiene información adicional, por ejemplo, si la regla está habilitada de forma predeterminada y si tiene asociado un *corrección de código*. ([Correcciones de código](../ide/quick-actions.md) están disponibles en el menú de icono de bombilla de Visual Studio con un solo clic correcciones.)

A partir de la fecha de esta página, la lista de FxCop reglas que se han trasladado a [analizadores de FxCop](install-fxcop-analyzers.md) incluye:

Identificador de la regla | Título
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | No declarar miembros estáticos en tipos genéricos
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Los tipos que poseen campos descartables deben ser descartables
[CA1003](ca1003-use-generic-event-handler-instances.md) | Utilizar instancias genéricas de controlador de eventos
[CA1008](ca1008-enums-should-have-zero-value.md) | Las enumeraciones deben tener un valor igual a cero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Las colecciones deben implementar la interfaz genérica
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Los tipos abstractos no deberían tener constructores
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Marque los ensamblados con CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Marque los ensamblados con la versión del ensamblado
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Marque los ensamblados con ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Marcar atributos con AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Definir descriptores de acceso para los argumentos de atributo
[CA1024](ca1024-use-properties-where-appropriate.md) | Utilizar las propiedades donde corresponda
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Marcar enumeraciones con FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | Almacenamiento de la enumeración debe ser de tipo Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Utilizar eventos cuando sea apropiado
[CA1031](ca1031-do-not-catch-general-exception-types.md) | No capturar los tipos de excepción general
[CA1032](ca1032-implement-standard-exception-constructors.md) | Implementar constructores de excepción estándar
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Los tipos secundarios deben poder llamar a los métodos de interfaz
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Los tipos anidados no deben ser visibles
[CA1036](ca1036-override-methods-on-comparable-types.md) | Invalidar métodos en tipos comparables
[CA1040](ca1040-avoid-empty-interfaces.md) | Evitar las interfaces vacías
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Proporcionar un mensaje ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Entero de uso o el argumento de cadena para los indizadores
[CA1044](ca1044-properties-should-not-be-write-only.md) | Las propiedades no deben ser de solo escritura
[CA1050](ca1050-declare-types-in-namespaces.md) | Declarar tipos en espacios de nombres
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | No declarar campos de instancia visibles
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Los tipos titulares estáticos deben ser estáticos o NotInheritable (vea la nota que sigue a esta tabla)
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Los tipos titulares estáticos no deben tener constructores (vea la nota que sigue a esta tabla)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Los parámetros de URI no deben ser cadenas
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | URI devuelven valores no deben ser cadenas
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Las propiedades URI no deben ser cadenas
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Los tipos no deben ampliar ciertos tipos base
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Mover elementos PInvoke a clases de métodos nativos
[CA1061](ca1061-do-not-hide-base-class-methods.md) | No ocultar métodos de clase base
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Validar argumentos de métodos públicos
[CA1063](ca1063-implement-idisposable-correctly.md) | Implemente IDisposable correctamente
[CA1064](ca1064-exceptions-should-be-public.md) | Las excepciones deben ser públicas
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | No producir excepciones en ubicaciones inesperadas
CA1066 | Tipo {0} deben implementar IEquatable<T> porque reemplaza Equals
CA1067 | Invalidar Object.Equals(object) al implementar IEquatable<T>
CA1068 | CancellationToken parámetros deben proceder último
CA1200 | Evite el uso de etiquetas de cref con un prefijo
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | No pasar literales como parámetros localizados
[CA1304](ca1304-specify-cultureinfo.md) | Especificar CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Especificar IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Especificar StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizar cadenas en mayúsculas
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Usar comparación de cadenas ordinales
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Los elementos P/Invoke no deben estar visibles
[CA1501](ca1501-avoid-excessive-inheritance.md) | Evitar una herencia excesiva
[CA1502](ca1502-avoid-excessive-complexity.md) | Evitar una complejidad excesiva
[CA1505](ca1505-avoid-unmaintainable-code.md) | Evitar código que no se puede mantener
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Evitar el acoplamiento excesivo de clases
[CA1507](ca1507.md) | Usar nameof para expresar los nombres de símbolos
CA1508 | Evitar código muerto condicional
CA1509 | Entrada no válida en el archivo de especificación de reglas de métricas de código
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Los identificadores no deben contener caracteres de subrayado
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Los identificadores deben tener un sufijo correcto
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Los identificadores no deben tener un sufijo incorrecto
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | No utilizar prefijos en valores de enumeración con el nombre del tipo
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Las enumeraciones Flags deben tener nombres en plural
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Los identificadores deben tener el prefijo correcto
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Los identificadores no deben coincidir con palabras clave
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Identificador contiene el nombre de tipo
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Los nombres de propiedades no deben coincidir con los métodos get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Los nombres de tipo no deberían coincidir con los espacios de nombres
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Los nombres de parámetro deben coincidir con la declaración base
[CA1801](ca1801-review-unused-parameters.md) | Revisar parámetros sin utilizar
[CA1802](ca1802-use-literals-where-appropriate.md) | Usar literales cuando sea apropiado
[CA1806](ca1806-do-not-ignore-method-results.md) | No omitir resultados del método
[CA1810](ca1810-initialize-reference-type-static-fields-inline.md) | Inicializar campos estáticos de tipo de referencia insertados
[CA1812](ca1812-avoid-uninstantiated-internal-classes.md) | Evitar las clases internas sin instancia
[CA1813](ca1813-avoid-unsealed-attributes.md) | Evitar los atributos no sellados
[CA1814](ca1814-prefer-jagged-arrays-over-multidimensional.md) | Preferir matrices escalonadas antes que multidimensionales
[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md) | Invalidar Equals y el operador Equals en los tipos de valores
[CA1816](ca1816-call-gc-suppressfinalize-correctly.md) | Los métodos Dispose deben llamar a SuppressFinalize
[CA1819](ca1819-properties-should-not-return-arrays.md) | Las propiedades no deben devolver matrices
[CA1820](ca1820-test-for-empty-strings-using-string-length.md) | Comprobar si las cadenas están vacías mediante la longitud de cadena
[CA1821](ca1821-remove-empty-finalizers.md) | Quitar los finalizadores vacíos
[CA1822](ca1822-mark-members-as-static.md) | Marcar miembros como estáticos
[CA1823](ca1823-avoid-unused-private-fields.md) | Evitar los campos privados sin utilizar
[CA1824](ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Marcar los ensamblados con NeutralResourcesLanguageAttribute
CA1825 | Evitar las asignaciones de la matriz de longitud cero.
CA1826 | No use métodos Enumerable en colecciones indexables. En su lugar, usar la colección directamente
[CA2000](ca2000-dispose-objects-before-losing-scope.md) | Desechar objetos antes de perder el ámbito
[CA2002](ca2002-do-not-lock-on-objects-with-weak-identity.md) | No bloquear objetos con identidad débil
[CA2007](ca2007-do-not-directly-await-task.md) | Considere la posibilidad de llamar a ConfigureAwait en la tarea en espera
CA2008 | No cree tareas sin pasar TaskScheduler
CA2009 | No llame a ToImmutableCollection en un valor ImmutableCollection
CA2010 | Consumir siempre el valor devuelto por los métodos marcados con PreserveSigAttribute
[CA2100](ca2100-review-sql-queries-for-security-vulnerabilities.md) | Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[CA2101](ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Especificar serialización en argumentos de cadena P/Invoke
[CA2119](ca2119-seal-methods-that-satisfy-private-interfaces.md) | Sellar los métodos que satisfacen las interfaces privadas
[CA2153](ca2153-avoid-handling-corrupted-state-exceptions.md) | No capturar excepciones de estado dañadas
[CA2200](ca2200-rethrow-to-preserve-stack-details.md) | Reiniciar para mantener los detalles de la pila.
[CA2201](ca2201-do-not-raise-reserved-exception-types.md) | No provocar tipos de excepción reservados
[CA2207](ca2207-initialize-value-type-static-fields-inline.md) | Inicializar campos estáticos de tipo de valor insertados
[CA2208](ca2208-instantiate-argument-exceptions-correctly.md) | Crear instancias de las excepciones del argumento correctamente
[CA2211](ca2211-non-constant-fields-should-not-be-visible.md) | Los campos no constantes no deben ser visibles
[CA2213](ca2213-disposable-fields-should-be-disposed.md) | Los campos descartables deben ser descartables
[CA2214](ca2214-do-not-call-overridable-methods-in-constructors.md) | No llamar a métodos reemplazables en constructores
[CA2216](ca2216-disposable-types-should-declare-finalizer.md) | Los tipos descartables deben declarar el finalizador
[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md) | No marcar enumeraciones con FlagsAttribute
[CA2218](ca2218-override-gethashcode-on-overriding-equals.md) | Invalidar el método GetHashCode al invalidar el método Equals
[CA2219](ca2219-do-not-raise-exceptions-in-exception-clauses.md) | No producir excepciones en cláusulas finally
[CA2224](ca2224-override-equals-on-overloading-operator-equals.md) | Invalidar Equals al sobrecargar operadores es igual a
[CA2225](ca2225-operator-overloads-have-named-alternates.md) | Las sobrecargas del operador tienen alternativas con nombre
[CA2226](ca2226-operators-should-have-symmetrical-overloads.md) | Los operadores deben tener sobrecargas simétricas
[CA2227](ca2227-collection-properties-should-be-read-only.md) | Las propiedades de la colección deben ser de solo lectura
[CA2229](ca2229-implement-serialization-constructors.md) | Implementar constructores de serialización
[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Sobrecarga del operador es igual al invalidar el valor de tipo es igual a
[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) | Pasar objetos de uri en lugar de cadenas de sistema
[CA2235](ca2235-mark-all-non-serializable-fields.md) | Marcar todos los campos no serializables
[CA2237](ca2237-mark-iserializable-types-with-serializableattribute.md) | Marcar los tipos ISerializable con serializable
[CA2241](ca2241-provide-correct-arguments-to-formatting-methods.md) | Proporcionar argumentos correctos a los métodos de formato
[CA2242](ca2242-test-for-nan-correctly.md) | Comprobar NaN correctamente
[CA2243](ca2243-attribute-string-literals-should-parse-correctly.md) | Los literales de cadena de atributo se deben analizar correctamente
CA2244 | No se duplican las inicializaciones de elemento indizado
[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md) | No usar el deserializador no seguro BinaryFormatter
[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) | No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder
[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) | Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize
[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md) | No usar el deserializador no seguro LosFormatter
[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md) | No usar el deserializador no seguro NetDataContractSerializer
[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) | No deserializar sin establecer primero NetDataContractSerializer.Binder
[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) | Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar
[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md) | No usar el deserializador no seguro ObjectStateFormatter
[CA2321](ca2321.md) | No deserializar con JavaScriptSerializer mediante SimpleTypeResolver
[CA2322](ca2322.md) | Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar
[CA3001](ca3001-review-code-for-sql-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de SQL
[CA3002](ca3002-review-code-for-xss-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de XSS
[CA3003](ca3003-review-code-for-file-path-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos
[CA3004](ca3004-review-code-for-information-disclosure-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de divulgación de información
[CA3005](ca3005-review-code-for-ldap-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de LDAP
[CA3006](ca3006-review-code-for-process-command-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos
[CA3007](ca3007-review-code-for-open-redirect-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de redireccionamiento abierto
[CA3008](ca3008-review-code-for-xpath-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de XPath
[CA3009](ca3009-review-code-for-xml-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de XML
[CA3010](ca3010-review-code-for-xaml-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de XAML
[CA3011](ca3011-review-code-for-dll-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de DLL
[CA3012](ca3012-review-code-for-regex-injection-vulnerabilities.md) | Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares
CA3061 | No agregue el esquema de dirección URL
[CA3075](ca3075-insecure-dtd-processing.md) | Procesamiento de DTD no seguro en XML
[CA3076](ca3076-insecure-xslt-script-execution.md) | Procesamiento de secuencias de comandos XSLT no seguro.
[CA3077](ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md) | Procesamiento inseguro en el diseño de API, XmlDocument y XmlTextReader
[CA3147](ca3147-mark-verb-handlers-with-validateantiforgerytoken.md) | Controladores de Mark verbo con validación el Token antifalsificación
[CA5350](ca5350-do-not-use-weak-cryptographic-algorithms.md) | No usar algoritmos criptográficos no seguros
[CA5351](ca5351-do-not-use-broken-cryptographic-algorithms.md) | No Use algoritmos criptográficos rotos
CA5358 | No Use modos de cifrado no seguros
CA5359 | No deshabilite la validación de certificados
CA5360 | No llame a métodos peligrosos en la deserialización
CA5361 | No deshabilite SChannel uso de criptografía fuerte
CA5362 | ¿Se refieren Self en una clase Serializable
CA5363 | Deshabilitar la validación de solicitudes
CA5364 | No Use protocolos de seguridad en desuso
CA5365 | Deshabilitar comprobación de encabezado de HTTP
CA5366 | Usar XmlReader para leer del conjunto de datos Xml
CA5367 | No se serializan los tipos con los campos de puntero
CA5368 | Establece ViewStateUserKey para clases derivadas de página
CA5369 | Usar XmlReader para deserializar
CA5370 | Usar XmlReader para lector de validación
CA5371 | Usar XmlReader para leer de esquema
CA5372 | Usar XmlReader para XPathDocument
CA5373 | No utilice la función de derivación de claves obsoleto
CA5374 | No Use XslTransform
CA5375 | No Use la firma de acceso compartido de cuenta
CA5376 | Usar httpsonly a SharedAccessProtocol
CA5377 | Usar la directiva de acceso de nivel de contenedor
CA5378 | No deshabilite ServicePointManagerSecurityProtocols
CA5379 | No Use el algoritmo de derivación de clave débil (función)
CA9999 | Discrepancia de versiones del analizador

> [!NOTE]
> CA1052 reglas y CA1053 de la implementación original de FxCop se combinan en una única regla, CA1052, en los analizadores de FxCop.

## <a name="unported-rules"></a>Reglas de protección

El conjunto de reglas que aún no se ha trasladado a [analizadores de FxCop](install-fxcop-analyzers.md) consta de reglas que no han migrado aún pero aún [se puede portar](#rules-that-may-be-ported)y aquellos que están en desuso y [no seráportada](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Reglas que se pueden portar

Las siguientes reglas de análisis de código estático de FxCop aún no ha implementado aún como analizadores, pero aún pueden ser. Esto podría ser debido a una bloquea razón técnica o simplemente que la regla es la prioridad más baja. Para obtener más información sobre el estado de migración de cada regla, haga clic en el vínculo en el **seguimiento problema** columna.

Identificador de la regla | Problema de seguimiento
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804-remove-unused-locals.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811-avoid-uncalled-private-code.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900-value-type-fields-should-be-portable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001-avoid-calling-problematic-methods.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004-remove-calls-to-gc-keepalive.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006-use-safehandle-to-encapsulate-native-resources.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109-review-visible-event-handlers.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204-literals-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205-use-managed-equivalents-of-win32-api.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212-do-not-mark-serviced-components-with-webmethod.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215-dispose-methods-should-call-base-class-dispose.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232-mark-windows-forms-entry-points-with-stathread.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236-call-base-class-methods-on-iserializable-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238-implement-serialization-methods-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239-provide-deserialization-methods-for-optional-fields.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240-implement-iserializable-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Reglas en desuso

Las siguientes reglas de análisis de código estático de FxCop están en desuso y no se pueden implementar como analizadores. Para obtener más información, puede buscar por Id. de regla (por ejemplo, **CA1009**) en el [página de problemas de GitHub de analizadores de roslyn](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702-compound-words-should-be-cased-correctly.md)
- [CA1703](ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1800](ca1800-do-not-cast-unnecessarily.md)
- [CA1809](ca1809-avoid-excessive-locals.md)
- [CA1901](ca1901-p-invoke-declarations-should-be-portable.md)
- [CA1903](ca1903-use-only-api-from-targeted-framework.md)
- [CA2003](ca2003-do-not-treat-fibers-as-threads.md)
- [CA2102](ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)
- [CA2103](ca2103-review-imperative-security.md)
- [CA2104](ca2104-do-not-declare-read-only-mutable-reference-types.md)
- [CA2105](ca2105-array-fields-should-not-be-read-only.md)
- [CA2106](ca2106-secure-asserts.md)
- [CA2107](ca2107-review-deny-and-permit-only-usage.md)
- [CA2108](ca2108-review-declarative-security-on-value-types.md)
- [CA2111](ca2111-pointers-should-not-be-visible.md)
- [CA2112](ca2112-secured-types-should-not-expose-fields.md)
- [CA2114](ca2114-method-security-should-be-a-superset-of-type.md)
- [CA2115](ca2115-call-gc-keepalive-when-using-native-resources.md)
- [CA2116](ca2116-aptca-methods-should-only-call-aptca-methods.md)
- [CA2117](ca2117-aptca-types-should-only-extend-aptca-base-types.md)
- [CA2118](ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)
- [CA2120](ca2120-secure-serialization-constructors.md)
- [CA2121](ca2121-static-constructors-should-be-private.md)
- [CA2122](ca2122-do-not-indirectly-expose-methods-with-link-demands.md)
- [CA2123](ca2123-override-link-demands-should-be-identical-to-base.md)
- [CA2124](ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)
- [CA2126](ca2126-type-link-demands-require-inheritance-demands.md)
- [CA2130](ca2130-security-critical-constants-should-be-transparent.md)
- [CA2131](ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)
- [CA2132](ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)
- [CA2133](ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)
- [CA2134](ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)
- [CA2135](ca2135-level-2-assemblies-should-not-contain-linkdemands.md)
- [CA2136](ca2136-members-should-not-have-conflicting-transparency-annotations.md)
- [CA2137](ca2137-transparent-methods-must-contain-only-verifiable-il.md)
- [CA2138](ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)
- [CA2139](ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)
- [CA2140](ca2140-transparent-code-must-not-reference-security-critical-items.md)
- [CA2141](ca2141-transparent-methods-must-not-satisfy-linkdemands.md)
- [CA2142](ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
- [CA2143](ca2143-transparent-methods-should-not-use-security-demands.md)
- [CA2144](ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)
- [CA2145](ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)
- [CA2146](ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)
- [CA2147](ca2147-transparent-methods-may-not-use-security-asserts.md)
- [CA2149](ca2149-transparent-methods-must-not-call-into-native-code.md)
- [CA2151](ca2151-fields-with-critical-types-should-be-security-critical.md)
- [CA2202](ca2202-do-not-dispose-objects-multiple-times.md)
- [CA2210](ca2210-assemblies-should-have-valid-strong-names.md)
- [CA2220](ca2220-finalizers-should-call-base-class-finalizer.md)
- [CA2221](ca2221-finalizers-should-be-protected.md)
- [CA2222](ca2222-do-not-decrease-inherited-member-visibility.md) ([justificación](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223-members-should-differ-by-more-than-return-type.md)
- [CA2228](ca2228-do-not-ship-unreleased-resource-formats.md)
- [CA2230](ca2230-use-params-for-variable-arguments.md)
- [CA2233](ca2233-operations-should-not-overflow.md)
- [CA5122](ca5122-p-invoke-declarations-should-not-be-safe-critical.md)

## <a name="see-also"></a>Vea también

- [Reglas de Microsoft.CodeAnalysis.FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)