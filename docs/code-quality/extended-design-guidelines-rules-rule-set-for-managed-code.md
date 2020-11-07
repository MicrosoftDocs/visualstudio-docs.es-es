---
title: Conjunto de reglas Reglas de directrices de diseño ampliadas para código administrado
ms.date: 11/04/2016
description: Obtenga información sobre el conjunto de reglas reglas de directrices de diseño extendido en Visual Studio, que se centra en la facilidad de uso y el mantenimiento. Vea las descripciones de las reglas.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0da23a533ca7667ba946299a3197dd487999afec
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348988"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de directrices de diseño ampliadas para código administrado

El conjunto de reglas reglas de directrices de diseño extendido de Microsoft amplía las reglas de directrices de diseño básicas para maximizar los problemas de facilidad de uso y mantenimiento que se indican. Se pone especial énfasis en las directrices de nomenclatura. Debe considerar la posibilidad de incluir este conjunto de reglas si el proyecto incluye código de biblioteca o si desea aplicar los estándares más altos para escribir código que sea fácil de mantener.

Las reglas de directrices de diseño extendidas incluyen todas las reglas del conjunto de reglas [reglas de directrices de diseño básicas](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , que incluye las reglas del conjunto de reglas [reglas recomendadas administradas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

En la tabla siguiente se describen todas las reglas del conjunto de reglas reglas de directrices de diseño extendido de Microsoft.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1009](../code-quality/ca1009.md)|Declarar los controladores de evento correctamente|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1049](../code-quality/ca1049.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|No ocultar métodos de clase base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementar IDisposable correctamente|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415.md)|Declarar elementos P/Invoke correctamente|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Quitar finalizadores vacíos|
|[CA1900](../code-quality/ca1900.md)|Los campos de tipo de valor deben ser portátiles|
|[CA1901](../code-quality/ca1901.md)|Las declaraciones P/Invoke deben ser portátiles|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|No bloquear objetos con identidad débil|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Especificar serialización en argumentos de cadena P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2111](../code-quality/ca2111.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2116](../code-quality/ca2116.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2122](../code-quality/ca2122.md)|No exponer indirectamente métodos con peticiones de vínculos|
|[CA2123](../code-quality/ca2123.md)|Las peticiones de vínculos de invalidaciones deben ser idénticas a la base|
|[CA2124](../code-quality/ca2124.md)|Incluir cláusulas finally vulnerables en un bloque try externo|
|[CA2126](../code-quality/ca2126.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2131](../code-quality/ca2131.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base|
|[CA2133](../code-quality/ca2133.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134.md)|Los métodos deben mantener una transparencia coherente al invalidar métodos base|
|[CA2137](../code-quality/ca2137.md)|Los métodos transparentes deben contener solo IL que se pueda comprobar|
|[CA2138](../code-quality/ca2138.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141.md)|Los métodos transparentes no deben satisfacer LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base|
|[CA2147](../code-quality/ca2147.md)|Los métodos transparentes no pueden usar aserciones de seguridad|
|[CA2149](../code-quality/ca2149.md)|Los métodos transparentes no deben llamar a código nativo|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Reiniciar para mantener los detalles de la pila|
|[CA2202](../code-quality/ca2202.md)|No usar Dispose varias veces en objetos|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Los campos descartables deben ser descartables|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|No llamar a métodos reemplazables en constructores|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementar constructores de serialización|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable correctamente|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Comprobar NaN correctamente|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|No declarar miembros estáticos en tipos genéricos|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|No exponer listas genéricas|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Utilizar instancias genéricas de controlador de eventos|
|[CA1004](../code-quality/ca1004.md)|Los métodos genéricos deben proporcionar un parámetro de tipo|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Evitar los parámetros excesivos en tipos genéricos|
|[CA1006](../code-quality/ca1006.md)|No anidar tipos genéricos en signaturas de miembro|
|[CA1007](../code-quality/ca1007.md)|Utilizar valores genéricos cuando sea posible|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Las enumeraciones deben tener un valor igual a cero|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Las colecciones deben implementar la interfaz genérica|
|[CA1011](../code-quality/ca1011.md)|Considerar pasar los tipos base como parámetros|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Los tipos abstractos no deberían tener constructores|
|[CA1013](../code-quality/ca1013.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Marcar los ensamblados con CLSCompliantAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Marcar los ensamblados con ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Marcar atributos con AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Definir descriptores de acceso para los argumentos de atributo|
|[CA1023](../code-quality/ca1023.md)|Los indizadores no deben ser multidimensionales|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Utilizar las propiedades donde corresponda|
|[CA1025](../code-quality/ca1025.md)|Reemplazar argumentos repetitivos por una matriz de parámetros|
|[CA1026](../code-quality/ca1026.md)|No deben usarse parámetros predeterminados|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Marcar enumeraciones con FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|El almacenamiento de la enumeración debe ser de tipo Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Utilizar eventos cuando sea apropiado|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|No capturar los tipos de excepción general|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementar constructores de excepción estándar|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Los tipos anidados no deben ser visibles|
|[CA1035](../code-quality/ca1035.md)|Las implementaciones de ICollection tienen miembros fuertemente tipados|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Invalidar métodos en tipos comparables|
|[CA1038](../code-quality/ca1038.md)|Los enumeradores deben estar fuertemente tipados|
|[CA1039](../code-quality/ca1039.md)|Las listas están fuertemente tipadas|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Proporcionar un mensaje ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Utilizar un argumento integral o de cadena en indizadores|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Las propiedades no deben ser de solo escritura|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|No sobrecargar el operador de igualdad en los tipos de referencia|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|No declarar miembros protegidos en tipos sellados|
|[CA1048](../code-quality/ca1048.md)|No declarar miembros virtuales en tipos sellados|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Declarar tipos en espacios de nombres|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|No declarar campos de instancia visibles|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Los tipos titulares estáticos deben estar sellados|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Los tipos titulares estáticos no deben tener constructores|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Los parámetros de URI no deben ser cadenas|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Los valores devueltos URI no deben ser cadenas|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Las propiedades URI no deben ser cadenas|
|[CA1057](../code-quality/ca1057.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Los tipos no deben ampliar ciertos tipos base|
|[CA1059](../code-quality/ca1059.md)|Los miembros no deben exponer algunos tipos concretos|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Las excepciones deben ser públicas|
|[CA1500](../code-quality/ca1500.md)|Los nombres de las variables no deben coincidir con los nombres de los campos|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Evitar una complejidad excesiva|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Los identificadores no deben coincidir con palabras clave|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Revisar parámetros sin utilizar|
|[CA1804](../code-quality/ca1804.md)|Quitar variables locales no utilizadas|
|[CA1809](../code-quality/ca1809.md)|Evitar las variables locales excesivas|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Inicializar campos estáticos de tipo de referencia insertados|
|[CA1811](../code-quality/ca1811.md)|Evitar código privado al que no se llama|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Evitar las clases internas sin instancia|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Evitar los atributos no sellados|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Preferir matrices escalonadas antes que multidimensionales|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Invalidar Equals y el operador Equals en los tipos de valores|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Las propiedades no deben devolver matrices|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Marcar miembros como estáticos|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Evitar los campos privados sin utilizar|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|No provocar tipos de excepción reservados|
|[CA2205](../code-quality/ca2205.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Crear instancias de las excepciones del argumento correctamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Los campos no constantes no deben ser visibles|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|No marcar enumeraciones con FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|No producir excepciones en cláusulas de excepción|
|[CA2221](../code-quality/ca2221.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Las sobrecargas del operador tienen alternativas con nombre|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Las propiedades de la colección deben ser de solo lectura|
|[CA2230](../code-quality/ca2230.md)|Usar parámetros en argumentos de variable|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Pasar objetos System.Uri en lugar de cadenas|
|[CA2239](../code-quality/ca2239.md)|Proporcionar métodos de deserialización para campos opcionales|
|[CA1020](../code-quality/ca1020.md)|Evitar los espacios de nombres con pocos tipos|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|Evitar los parámetros out|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|Evitar las interfaces vacías|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|No pasar tipos por referencia|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|Validar argumentos de métodos públicos|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|Evitar una herencia excesiva|
|[CA1504](../code-quality/ca1504.md)|Revisar los nombres de campos erróneos|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|Evitar código que no se puede mantener|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|Evitar el acoplamiento excesivo de clases|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|No nombrar valores de enumeración como 'Reserved'|
|[CA1701](../code-quality/ca1701.md)|En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente|
|[CA1702](../code-quality/ca1702.md)|En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente|
|[CA1703](../code-quality/ca1703.md)|La ortografía de las cadenas de recursos debe ser correcta|
|[CA1704](../code-quality/ca1704.md)|La ortografía de los identificadores debe ser correcta|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|Los identificadores no deben contener caracteres de subrayado|
|[CA1709](../code-quality/ca1709.md)|Los identificadores deben utilizar las mayúsculas y minúsculas correctamente|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|Los identificadores deben tener un sufijo correcto|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|Los identificadores no deben tener un sufijo incorrecto|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|No utilizar prefijos en valores de enumeración con el nombre del tipo|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|Los eventos no deben tener prefijos antes ni después|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|Las enumeraciones Flags deben tener nombres en plural|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|Los identificadores deben tener el prefijo correcto|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|Solo las enumeraciones FlagsAttribute deben tener nombres en plural|
|[CA1719](../code-quality/ca1719.md)|Los nombres de parámetro no deben coincidir con los nombres de miembro|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|Los identificadores no deben contener nombres de tipo|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|Los nombres de propiedades no deben coincidir con los métodos get|
|[CA1722](../code-quality/ca1722.md)|Los identificadores no deben tener un prefijo incorrecto|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|Los nombres de tipo no deben coincidir con los espacios de nombres|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|Los nombres de parámetro deben coincidir con la declaración base|
|[CA1726](../code-quality/ca1726.md)|Utilizar términos preferidos|
|[CA2204](../code-quality/ca2204.md)|Los literales deben estar escritos correctamente|
