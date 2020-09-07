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
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508371"
---
# <a name="fxcop-rule-port-status"></a>Estado del puerto de la regla de FxCop

Si anteriormente usó el análisis de código estático en Visual Studio, es posible que se pregunte qué reglas están disponibles en la implementación actual como [analizadores de FxCop](install-fxcop-analyzers.md). En esta página se enumeran las reglas que se han trasladado. Vea [reglas no trasladadas](fxcop-unported-rules.md) para aquellas que no se han migrado y si hay planes para trasladarlas.

## <a name="ported-rules"></a>Reglas migradas

La [Página de documentación autogenerada](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) del repositorio Roslyn-analizadores tiene la lista más actualizada de reglas que se han trasladado a los analizadores de FxCop. Esa página también tiene información adicional, por ejemplo, si la regla está habilitada de forma predeterminada y si tiene una *corrección de código*asociada. (Las[correcciones de código](../ide/quick-actions.md) son correcciones con un solo clic disponibles en el menú del icono de bombilla de Visual Studio).

A partir de la fecha de esta página, la lista de reglas de FxCop que se han trasladado a los [analizadores de FxCop](install-fxcop-analyzers.md) incluye:

Id. de regla | Title
--------|---------
[CA1000](ca1000.md) | No declarar miembros estáticos en tipos genéricos
[CA1001](ca1001.md) | Los tipos que poseen campos descartables deben ser descartables
[CA1002](ca1002.md) | No exponer listas genéricas
[CA1003](ca1003.md) | Utilizar instancias genéricas de controlador de eventos
[CA1005](ca1005.md) | Evitar los parámetros excesivos en tipos genéricos
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
[CA1045](ca1045.md) | No pasar tipos por referencia
[CA1046](ca1046.md) | No sobrecargar el operador de igualdad en los tipos de referencia
[CA1047](ca1047.md) | No declarar miembros protegidos en tipos sellados
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
[CA1700](ca1700.md) | No nombrar valores de enumeración como 'Reserved'
[CA1707](ca1707.md) | Los identificadores no deben contener caracteres de subrayado
[CA1708](ca1708.md) | Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas
[CA1710](ca1710.md) | Los identificadores deben tener un sufijo correcto
[CA1711](ca1711.md) | Los identificadores no deben tener un sufijo incorrecto
[CA1712](ca1712.md) | No utilizar prefijos en valores de enumeración con el nombre del tipo
[CA1713](ca1713.md) | Los eventos no deben tener prefijos antes ni después
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
[CA1805](ca1805.md) | No inicializar innecesariamente
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
[CA2000](ca2000.md) | Desechar objetos antes de perder el ámbito
[CA2002](ca2002.md) | No bloquear objetos con identidad débil
[CA2100](ca2100.md) | Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[CA2101](ca2101.md) | Especificar serialización en argumentos de cadena P/Invoke
[CA2109](ca2109.md) | Revisar los controladores de eventos visibles
[CA2119](ca2119.md) | Sellar los métodos que satisfacen las interfaces privadas
[CA2153](ca2153.md) | No capturar excepciones de estado dañadas
[CA2200](ca2200.md) | Vuelva a iniciar para conservar los detalles de la pila.
[CA2201](ca2201.md) | No provocar tipos de excepción reservados
[CA2207](ca2207.md) | Inicializar campos estáticos de tipo de valor insertados
[CA2208](ca2208.md) | Crear instancias de las excepciones del argumento correctamente
[CA2211](ca2211.md) | Los campos no constantes no deben ser visibles
[CA2213](ca2213.md) | Los campos descartables deben ser descartables
[CA2214](ca2214.md) | No llamar a métodos reemplazables en constructores
[CA2215](ca2215.md) | Los métodos Dispose deben llamar al método Dispose de la clase base
[CA2216](ca2216.md) | Los tipos descartables deben declarar el finalizador
[CA2217](ca2217.md) | No marcar enumeraciones con FlagsAttribute
[CA2219](ca2219.md) | No producir excepciones en cláusulas Finally
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

## <a name="see-also"></a>Vea también

- [Reglas de Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
