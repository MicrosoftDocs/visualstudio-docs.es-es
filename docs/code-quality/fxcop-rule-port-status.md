---
title: Estado del puerto de la regla de FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c3d9c1dfa45251d0f64a93bb9a5142dcec76b7c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89219730"
---
# <a name="fxcop-rule-port-status"></a>Estado del puerto de la regla de FxCop

Si anteriormente usó el análisis de código estático en Visual Studio, es posible que se pregunte qué reglas están disponibles en la implementación actual como [analizadores de FxCop](install-fxcop-analyzers.md). En esta página se enumeran las reglas que se portan, así como las que no se han migrado y si hay planes para trasladarlas.

## <a name="ported-rules"></a>Reglas migradas

La [Página de documentación autogenerada](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) del repositorio Roslyn-analizadores tiene la lista más actualizada de reglas que se han trasladado a los analizadores de FxCop. Esa página también tiene información adicional, por ejemplo, si la regla está habilitada de forma predeterminada y si tiene una *corrección de código*asociada. (Las[correcciones de código](../ide/quick-actions.md) son correcciones con un solo clic disponibles en el menú del icono de bombilla de Visual Studio).

A partir de la fecha de esta página, la lista de reglas de FxCop que se han trasladado a los [analizadores de FxCop](install-fxcop-analyzers.md) incluye:

Id. de regla | Título
--------|---------
[CA1000](ca1000.md) | No declarar miembros estáticos en tipos genéricos
[CA1001](ca1001.md) | Los tipos que poseen campos descartables deben ser descartables
[CA1003](ca1003.md) | Utilizar instancias genéricas de controlador de eventos
[CA1008](ca1008.md) | Las enumeraciones deben tener un valor igual a cero
[CA1010](ca1010.md) | Las colecciones deben implementar la interfaz genérica
[CA1012](ca1012.md) | Los tipos abstractos no deberían tener constructores
[CA1014](ca1014.md) | Marcar ensamblados con CLSCompliant
[CA1016](ca1016.md) | Marcar ensamblados con versión de ensamblado
[CA1017](ca1017.md) | Marcar ensamblados con ComVisible
[CA1018](ca1018.md) | Marcar atributos con AttributeUsageAttribute
[CA1019](ca1019.md) | Definir descriptores de acceso para los argumentos de atributo
[CA1021](ca1021.md) | Evitar los parámetros out
[CA1024](ca1024.md) | Utilizar las propiedades donde corresponda
[CA1027](ca1027.md) | Marcar enumeraciones con FlagsAttribute
[CA1028](ca1028.md) | El almacenamiento de enumeración debe ser Int32
[CA1030](ca1030.md) | Utilizar eventos cuando sea apropiado
[CA1031](ca1031.md) | No capturar los tipos de excepción general
[CA1032](ca1032.md) | Implementar constructores de excepción estándar
[CA1033](ca1033.md) | Los tipos secundarios deben poder llamar a los métodos de interfaz
[CA1034](ca1034.md) | Los tipos anidados no deben ser visibles
[CA1036](ca1036.md) | Invalidar métodos en tipos comparables
[CA1040](ca1040.md) | Evitar las interfaces vacías
[CA1041](ca1041.md) | Proporcionar un mensaje ObsoleteAttribute
[CA1043](ca1043.md) | Usar el argumento integral o de cadena para los indizadores
[CA1044](ca1044.md) | Las propiedades no deben ser de solo escritura
[CA1050](ca1050.md) | Declarar tipos en espacios de nombres
[CA1051](ca1051.md) | No declarar campos de instancia visibles
[CA1052](ca1052.md) | Los tipos de titulares estáticos deben ser estáticos o NotInheritable
[CA1053](ca1053.md) | Los tipos de titulares estáticos no deben tener constructores (CA1053 es parte de [CA1052](ca1052.md) para los analizadores de FxCop)
[CA1054](ca1054.md) | Los parámetros de URI no deben ser cadenas
[CA1055](ca1055.md) | Los valores devueltos de URI no deben ser cadenas
[CA1056](ca1056.md) | Las propiedades URI no deben ser cadenas
[CA1058](ca1058.md) | Los tipos no deben ampliar ciertos tipos base
[CA1060](ca1060.md) | Move pinvokes a la clase de métodos nativos
[CA1061](ca1061.md) | No ocultar métodos de clase base
[CA1062](ca1062.md) | Validar argumentos de métodos públicos
[CA1063](ca1063.md) | Implementar IDisposable correctamente
[CA1064](ca1064.md) | Las excepciones deben ser públicas
[CA1065](ca1065.md) | No producir excepciones en ubicaciones inesperadas
[CA1066](ca1066.md) | El tipo {0} debe implementar IEquatable \<T> porque invalida Equals
[CA1067](ca1067.md) | Invalidar Object. Equals (Object) al implementar IEquatable\<T>
[CA1068](ca1068.md) | Los parámetros CancellationToken deben aparecer en último lugar
CA1200 | Evitar el uso de etiquetas cref con un prefijo
[CA1303](ca1303.md) | No pasar literales como parámetros localizados
[CA1304](ca1304.md) | Especificar CultureInfo
[CA1305](ca1305.md) | Especificar IFormatProvider
[CA1307](ca1307.md) | Especificar StringComparison para mayor claridad
[CA1308](ca1308.md) | Normalizar cadenas en mayúsculas
[CA1309](ca1309.md) | Usar comparación de cadenas ordinales
[CA1401](ca1401.md) | Los elementos P/Invoke no deben estar visibles
[CA1501](ca1501.md) | Evitar una herencia excesiva
[CA1502](ca1502.md) | Evitar una complejidad excesiva
[CA1505](ca1505.md) | Evitar código que no se puede mantener
[CA1506](ca1506.md) | Evitar el acoplamiento excesivo de clases
[CA1507](ca1507.md) | Usar nombre para expresar nombres de símbolos
[CA1508](ca1508.md) | Evitar código condicional inactivo
CA1509 | Entrada no válida en el archivo de especificación de regla de métricas de código
[CA1707](ca1707.md) | Los identificadores no deben contener caracteres de subrayado
[CA1708](ca1708.md) | Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas
[CA1710](ca1710.md) | Los identificadores deben tener un sufijo correcto
[CA1711](ca1711.md) | Los identificadores no deben tener un sufijo incorrecto
[CA1712](ca1712.md) | No utilizar prefijos en valores de enumeración con el nombre del tipo
[CA1714](ca1714.md) | Las enumeraciones Flags deben tener nombres en plural
[CA1715](ca1715.md) | Los identificadores deben tener el prefijo correcto
[CA1716](ca1716.md) | Los identificadores no deben coincidir con palabras clave
[CA1717](ca1717.md) | Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[CA1720](ca1720.md) | El identificador contiene el nombre de tipo
[CA1721](ca1721.md) | Los nombres de propiedades no deben coincidir con los métodos get
[CA1724](ca1724.md) | Los nombres de tipo no deben coincidir con los espacios de nombres
[CA1725](ca1725.md) | Los nombres de parámetro deben coincidir con la declaración base
[CA1801](ca1801.md) | Revisar parámetros sin utilizar
[CA1802](ca1802.md) | Usar literales cuando corresponda
[CA1806](ca1806.md) | No omitir resultados del método
[CA1810](ca1810.md) | Inicializar campos estáticos de tipo de referencia insertados
[CA1812](ca1812.md) | Evitar las clases internas sin instancia
[CA1813](ca1813.md) | Evitar los atributos no sellados
[CA1814](ca1814.md) | Preferir matrices escalonadas antes que multidimensionales
[CA1815](ca1815.md) | Invalidar Equals y el operador Equals en los tipos de valores
[CA1816](ca1816.md) | Los métodos Dispose deben llamar a SuppressFinalize
[CA1819](ca1819.md) | Las propiedades no deben devolver matrices
[CA1820](ca1820.md) | Comprobar si las cadenas están vacías mediante la longitud de cadena
[CA1821](ca1821.md) | Quitar finalizadores vacíos
[CA1822](ca1822.md) | Marcar miembros como estáticos
[CA1823](ca1823.md) | Evitar los campos privados sin utilizar
[CA1824](ca1824.md) | Marcar los ensamblados con NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | Evite las asignaciones de matrices de longitud cero.
CA1826 | No use métodos enumerables en colecciones indizables. En su lugar, use la colección directamente
[CA2000](ca2000.md) | Desechar objetos antes de perder el ámbito
[CA2002](ca2002.md) | No bloquear objetos con identidad débil
[CA2007](ca2007.md) | Considere la posibilidad de llamar a ConfigureAwait en la tarea esperada
[CA2008](ca2008.md) | No crear tareas sin pasar un TaskScheduler
CA2009 | No llamar a ToImmutableCollection en un valor de ImmutableCollection
CA2010 | Usar siempre el valor devuelto por los métodos marcados con PreserveSigAttribute
[CA2100](ca2100.md) | Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[CA2101](ca2101.md) | Especificar serialización en argumentos de cadena P/Invoke
[CA2119](ca2119.md) | Sellar los métodos que satisfacen las interfaces privadas
[CA2153](ca2153.md) | No capturar excepciones de estado dañadas
[CA2200](ca2200.md) | Vuelva a iniciar para conservar los detalles de la pila.
[CA2201](ca2201.md) | No provocar tipos de excepción reservados
[CA2207](ca2207.md) | Inicializar campos estáticos de tipo de valor insertados
[CA2208](ca2208.md) | Crear instancias de las excepciones del argumento correctamente
[CA2211](ca2211.md) | Los campos no constantes no deben ser visibles
[CA2213](ca2213.md) | Los campos descartables deben ser descartables
[CA2214](ca2214.md) | No llamar a métodos reemplazables en constructores
[CA2216](ca2216.md) | Los tipos descartables deben declarar el finalizador
[CA2217](ca2217.md) | No marcar enumeraciones con FlagsAttribute
[CA2218](ca2218.md) | Invalidar el método GetHashCode al invalidar el método Equals
[CA2219](ca2219.md) | No producir excepciones en cláusulas Finally
[CA2224](ca2224.md) | Invalidar Equals al sobrecargar el operador Equals
[CA2225](ca2225.md) | Las sobrecargas del operador tienen alternativas con nombre
[CA2226](ca2226.md) | Los operadores deben tener sobrecargas simétricas
[CA2227](ca2227.md) | Las propiedades de la colección deben ser de solo lectura
[CA2229](ca2229.md) | Implementar constructores de serialización
[CA2231](ca2231.md) | Sobrecargar el operador de igualdad al reemplazar el tipo de valor es igual a
[CA2234](ca2234.md) | Pasar objetos URI del sistema en lugar de cadenas
[CA2235](ca2235.md) | Marcar todos los campos no serializables
[CA2237](ca2237.md) | Marcar los tipos ISerializable con serializable
[CA2241](ca2241.md) | Proporcionar argumentos correctos a los métodos de formato
[CA2242](ca2242.md) | Comprobar NaN correctamente
[CA2243](ca2243.md) | Los literales de cadena de atributo se deben analizar correctamente
CA2244 | No duplicar inicializaciones de elementos indizados
[CA2300](ca2300.md) | No usar el deserializador no seguro BinaryFormatter
[CA2301](ca2301.md) | No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder
[CA2302](ca2302.md) | Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize
[CA2305](ca2305.md) | No usar el deserializador no seguro LosFormatter
[CA2310](ca2310.md) | No usar el deserializador no seguro NetDataContractSerializer
[CA2311](ca2311.md) | No deserializar sin establecer primero NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar
[CA2315](ca2315.md) | No usar el deserializador no seguro ObjectStateFormatter
[CA2321](ca2321.md) | No deserializar con JavaScriptSerializer mediante SimpleTypeResolver
[CA2322](ca2322.md) | Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar
[CA3001](ca3001.md) | Revisión de código en busca de vulnerabilidades de inyección de SQL
[CA3002](ca3002.md) | Revisión de código en busca de vulnerabilidades de XSS
[CA3003](ca3003.md) | Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos
[CA3004](ca3004.md) | Revisión de código en busca de vulnerabilidades de divulgación de información
[CA3005](ca3005.md) | Revisión de código en busca de vulnerabilidades de inyección de LDAP
[CA3006](ca3006.md) | Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos
[CA3007](ca3007.md) | Revisión de código en busca de vulnerabilidades de redireccionamiento abierto
[CA3008](ca3008.md) | Revisión de código en busca de vulnerabilidades de inyección de XPath
[CA3009](ca3009.md) | Revisión de código en busca de vulnerabilidades de inyección de XML
[CA3010](ca3010.md) | Revisión de código en busca de vulnerabilidades de inyección de XAML
[CA3011](ca3011.md) | Revisión de código en busca de vulnerabilidades de inyección de DLL
[CA3012](ca3012.md) | Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares
[CA3061](ca3061.md) | No agregar esquema por dirección URL
[CA3075](ca3075.md) | Procesamiento de DTD no seguro en XML
[CA3076](ca3076.md) | Procesamiento de script XSLT no seguro.
[CA3077](ca3077.md) | Procesamiento inseguro en el diseño de API, XmlDocument y XmlTextReader
[CA3147](ca3147.md) | Marcar los controladores de verbos con validar token antifalsificación
[CA5350](ca5350.md) | No usar algoritmos criptográficos no seguros
[CA5351](ca5351.md) | No usar algoritmos criptográficos rotos
[CA5358](ca5358.md) | No usar modos de cifrado inseguro
CA5359 | No deshabilitar la validación de certificados
CA5360 | No llamar a métodos peligrosos en la deserialización
[CA5361](ca5361.md) | No deshabilite el uso de SChannel de cifrado seguro
CA5362 | No hacer referencia a sí mismo en una clase serializable
[CA5363](ca5363.md) | No deshabilitar la validación de solicitudes
[CA5364](ca5364.md) | No usar protocolos de seguridad en desuso
CA5365 | No deshabilitar la comprobación de encabezados HTTP
CA5366 | Usar XmlReader para leer el XML de DataSet
CA5367 | No serializar tipos con campos de puntero
CA5368 | Establecer ViewStateUserKey para las clases derivadas de Page
[CA5369](ca5369.md) | Usar XmlReader para deserializar
[CA5370](ca5370.md) | Usar XmlReader para validar el lector
[CA5371](ca5371.md) | Usar XmlReader para leer el esquema
[CA5372](ca5372.md) | Usar XmlReader para XPathDocument
[CA5373](ca5373.md) | No usar la función de derivación de clave obsoleta
CA5374 | No usar XslTransform
CA5375 | No usar firma de acceso compartido de cuenta
CA5376 | Uso de SharedAccessProtocol HttpsOnly
CA5377 | Usar la Directiva de acceso de nivel de contenedor
[CA5378](ca5378.md) | No deshabilitar ServicePointManagerSecurityProtocols
CA5379 | No usar algoritmo de función de derivación de clave débil
CA9999 | Versión de analizador no coincidente

## <a name="unported-rules"></a>Reglas no trasladadas

El conjunto de reglas que no se han migrado a los [analizadores de FxCop](install-fxcop-analyzers.md) consta de reglas que todavía no se [pueden portar](#rules-that-may-be-ported)y que están desusadas y que [no se portan](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Reglas que se pueden portar

Las siguientes reglas de análisis heredado de FxCop todavía no se han implementado como analizadores, pero todavía pueden ser. Esto puede deberse a una razón técnica de bloqueo o simplemente a que la regla tiene una prioridad más baja. Para obtener más información acerca del estado de portabilidad de cada regla, haga clic en el vínculo de la columna **problema de seguimiento** .

Id. de regla | Problema de seguimiento
--- | ---
[CA1002](ca1002.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Reglas en desuso

Las siguientes reglas de análisis heredado de FxCop están desusadas y no se implementarán como analizadores. Para obtener más información, puede buscar por el identificador de regla (por ejemplo, **CA1009**) en la [Página de problemas de github Roslyn-analizadores](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009.md)
- [CA1020](ca1020.md)
- [CA1025](ca1025.md)
- [CA1026](ca1026.md)
- [CA1035](ca1035.md)
- [CA1038](ca1038.md)
- [CA1039](ca1039.md)
- [CA1059](ca1059.md)
- [CA1302](ca1302.md)
- [CA1400](ca1400.md)
- [CA1406](ca1406.md)
- [CA1504](ca1504.md)
- [CA1701](ca1701.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([justificación](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Consulte también

- [Reglas de Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
