---
title: Estado del puerto de la regla de FxCop
ms.date: 05/21/2019
description: Obtenga información sobre las reglas de análisis de código estático que se han trasladado a analizadores de .NET en Visual Studio. Ver las reglas y los recursos trasladados en las actualizaciones de portabilidad.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: de23f3529cfcd321b0a7c3f9844ac69d96fed9c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860326"
---
# <a name="fxcop-rule-port-status"></a>Estado del puerto de la regla de FxCop

Si anteriormente usó el análisis de código estático en Visual Studio, es posible que se pregunte qué reglas están disponibles en la implementación actual como [analizadores de .net](install-net-analyzers.md). En esta página se enumeran las reglas que se han trasladado. Vea [reglas no trasladadas](fxcop-unported-rules.md) para aquellas que no se han migrado y si hay planes para trasladarlas.

## <a name="ported-rules"></a>Reglas migradas

La [Página de documentación autogenerada](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) en el repositorio Roslyn-analizadores tiene la lista más actualizada de reglas que se han trasladado a los analizadores de Roslyn. Esa página también tiene información adicional, por ejemplo, si la regla está habilitada de forma predeterminada y si tiene una *corrección de código* asociada. (Las[correcciones de código](../ide/quick-actions.md) son correcciones con un solo clic disponibles en el menú del icono de bombilla de Visual Studio).

A partir de la fecha de esta página, la lista de reglas de FxCop que se han trasladado a [analizadores de .net](install-net-analyzers.md) incluye:

Id. de regla | Título
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | No declarar miembros estáticos en tipos genéricos
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Los tipos que poseen campos descartables deben ser descartables
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | No exponer listas genéricas
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Utilizar instancias genéricas de controlador de eventos
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Evitar los parámetros excesivos en tipos genéricos
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Las enumeraciones deben tener un valor igual a cero
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Las colecciones deben implementar la interfaz genérica
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Los tipos abstractos no deberían tener constructores
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Marcar ensamblados con CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Marcar ensamblados con versión de ensamblado
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Marcar ensamblados con ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Marcar atributos con AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Definir descriptores de acceso para los argumentos de atributo
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Evitar los parámetros out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Utilizar las propiedades donde corresponda
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Marcar enumeraciones con FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | El almacenamiento de enumeración debe ser Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Utilizar eventos cuando sea apropiado
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | No capturar los tipos de excepción general
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Implementar constructores de excepción estándar
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Los tipos secundarios deben poder llamar a los métodos de interfaz
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Los tipos anidados no deben ser visibles
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Invalidar métodos en tipos comparables
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Evitar las interfaces vacías
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Proporcionar un mensaje ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Usar el argumento integral o de cadena para los indizadores
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Las propiedades no deben ser de solo escritura
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | No pasar tipos por referencia
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | No sobrecargar el operador de igualdad en los tipos de referencia
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | No declarar miembros protegidos en tipos sellados
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Declarar tipos en espacios de nombres
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | No declarar campos de instancia visibles
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Los tipos de titulares estáticos deben ser estáticos o NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Los tipos de titulares estáticos no deben tener constructores (CA1053 es parte de [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) para los analizadores de .net)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Los parámetros de URI no deben ser cadenas
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Los valores devueltos de URI no deben ser cadenas
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Las propiedades URI no deben ser cadenas
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Los tipos no deben ampliar ciertos tipos base
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Move pinvokes a la clase de métodos nativos
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | No ocultar métodos de clase base
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Validar argumentos de métodos públicos
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Implementar IDisposable correctamente
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Las excepciones deben ser públicas
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | No producir excepciones en ubicaciones inesperadas
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | El tipo {0} debe implementar IEquatable \<T> porque invalida Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Invalidar Object. Equals (Object) al implementar IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | No pasar literales como parámetros localizados
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Especificar CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Especificar IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Especificar StringComparison para mayor claridad
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normalizar cadenas en mayúsculas
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Usar comparación de cadenas ordinales
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | Los elementos P/Invoke no deben estar visibles
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Evitar una herencia excesiva
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Evitar una complejidad excesiva
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Evitar código que no se puede mantener
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Evitar el acoplamiento excesivo de clases
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | No nombrar valores de enumeración como 'Reserved'
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Los identificadores no deben contener caracteres de subrayado
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Los identificadores deben tener un sufijo correcto
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Los identificadores no deben tener un sufijo incorrecto
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | No utilizar prefijos en valores de enumeración con el nombre del tipo
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Los eventos no deben tener prefijos antes ni después
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Las enumeraciones Flags deben tener nombres en plural
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Los identificadores deben tener el prefijo correcto
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Los identificadores no deben coincidir con palabras clave
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | El identificador contiene el nombre de tipo
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Los nombres de propiedades no deben coincidir con los métodos get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Los nombres de tipo no deben coincidir con los espacios de nombres
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Los nombres de parámetro deben coincidir con la declaración base
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Revisar parámetros sin utilizar
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Usar literales cuando corresponda
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | No inicializar innecesariamente
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | No omitir resultados del método
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Inicializar campos estáticos de tipo de referencia insertados
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Evitar las clases internas sin instancia
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Evitar los atributos no sellados
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Preferir matrices escalonadas antes que multidimensionales
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Invalidar Equals y el operador Equals en los tipos de valores
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Los métodos Dispose deben llamar a SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Las propiedades no deben devolver matrices
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Comprobar si las cadenas están vacías mediante la longitud de cadena
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Quitar finalizadores vacíos
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Marcar miembros como estáticos
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Evitar los campos privados sin utilizar
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Marcar los ensamblados con NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Evite las asignaciones de matrices de longitud cero.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Desechar objetos antes de perder el ámbito
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | No bloquear objetos con identidad débil
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Especificar serialización en argumentos de cadena P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Revisar los controladores de eventos visibles
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Sellar los métodos que satisfacen las interfaces privadas
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | No capturar excepciones de estado dañadas
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Vuelva a iniciar para conservar los detalles de la pila.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | No provocar tipos de excepción reservados
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Inicializar campos estáticos de tipo de valor insertados
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Crear instancias de las excepciones del argumento correctamente
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Los campos no constantes no deben ser visibles
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Los campos descartables deben ser descartables
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | No llamar a métodos reemplazables en constructores
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Los métodos Dispose deben llamar al método Dispose de la clase base
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Los tipos descartables deben declarar el finalizador
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | No marcar enumeraciones con FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | No producir excepciones en cláusulas Finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Las sobrecargas del operador tienen alternativas con nombre
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Los operadores deben tener sobrecargas simétricas
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Las propiedades de la colección deben ser de solo lectura
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Implementar constructores de serialización
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Sobrecargar el operador de igualdad al reemplazar el tipo de valor es igual a
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Pasar objetos URI del sistema en lugar de cadenas
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Marcar todos los campos no serializables
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Marcar los tipos ISerializable con serializable
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Proporcionar argumentos correctos a los métodos de formato
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Comprobar NaN correctamente
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Los literales de cadena de atributo se deben analizar correctamente
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | No usar el deserializador no seguro BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | No usar el deserializador no seguro LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | No usar el deserializador no seguro NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | No deserializar sin establecer primero NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | No usar el deserializador no seguro ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | No deserializar con JavaScriptSerializer mediante SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Revisión de código en busca de vulnerabilidades de inyección de SQL
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Revisión de código en busca de vulnerabilidades de XSS
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Revisión de código en busca de vulnerabilidades de divulgación de información
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Revisión de código en busca de vulnerabilidades de inyección de LDAP
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Revisión de código en busca de vulnerabilidades de redireccionamiento abierto
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Revisión de código en busca de vulnerabilidades de inyección de XPath
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Revisión de código en busca de vulnerabilidades de inyección de XML
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Revisión de código en busca de vulnerabilidades de inyección de XAML
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Revisión de código en busca de vulnerabilidades de inyección de DLL
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | No agregar esquema por dirección URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Procesamiento de DTD no seguro en XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Procesamiento de script XSLT no seguro.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Procesamiento inseguro en el diseño de API, XmlDocument y XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Marcar los controladores de verbos con validar token antifalsificación
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | No usar algoritmos criptográficos no seguros
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | No usar algoritmos criptográficos rotos
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | No usar modos de cifrado inseguro
CA5359 | No deshabilitar la validación de certificados
CA5360 | No llamar a métodos peligrosos en la deserialización
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | No deshabilite el uso de SChannel de cifrado seguro
CA5362 | No hacer referencia a sí mismo en una clase serializable
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | No deshabilitar la validación de solicitudes
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | No usar protocolos de seguridad en desuso
CA5365 | No deshabilitar la comprobación de encabezados HTTP
CA5366 | Usar XmlReader para leer el XML de DataSet
CA5367 | No serializar tipos con campos de puntero
CA5368 | Establecer ViewStateUserKey para las clases derivadas de Page
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Usar XmlReader para deserializar
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Usar XmlReader para validar el lector
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Usar XmlReader para leer el esquema
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Usar XmlReader para XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | No usar la función de derivación de clave obsoleta
CA5374 | No usar XslTransform
CA5375 | No usar firma de acceso compartido de cuenta
CA5376 | Uso de SharedAccessProtocol HttpsOnly
CA5377 | Usar la Directiva de acceso de nivel de contenedor
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | No deshabilitar ServicePointManagerSecurityProtocols
CA5379 | No usar algoritmo de función de derivación de clave débil
CA9999 | Versión de analizador no coincidente

## <a name="see-also"></a>Vea también

- [Reglas del analizador de .NET](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
