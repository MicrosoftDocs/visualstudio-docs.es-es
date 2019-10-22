---
title: Conjunto de reglas Reglas de directrices de diseño básicas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: adc461e9620641084ce8a7fabc7b5a06c8a3bb73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608834"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de directrices de diseño básicas para código administrado

Puede usar el conjunto de reglas reglas de directrices de diseño básico de Microsoft para centrarse en facilitar la comprensión y el uso del código. Debe incluir este conjunto de reglas si el proyecto incluye código de biblioteca o si desea aplicar las prácticas recomendadas para el código que sea fácil de mantener.

Las reglas de directrices de diseño básicas incluyen todas las reglas del conjunto de reglas [reglas recomendadas administradas](managed-recommended-rules-rule-set-for-managed-code.md) .

En la tabla siguiente se describen todas las reglas del conjunto de reglas reglas de directrices de diseño básicas de Microsoft.

|Regla|Descripción|
|----------|-----------------|
|[CA1000](../code-quality/ca1000.md)|No declarar miembros estáticos en tipos genéricos|
|[CA1001](../code-quality/ca1001.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1002](../code-quality/ca1002.md)|No exponer listas genéricas|
|[CA1003](../code-quality/ca1003.md)|Utilizar instancias genéricas de controlador de eventos|
|[CA1004](../code-quality/ca1004.md)|Los métodos genéricos deben proporcionar un parámetro de tipo|
|[CA1005](../code-quality/ca1005.md)|Evitar los parámetros excesivos en tipos genéricos|
|[CA1006](../code-quality/ca1006.md)|No anidar tipos genéricos en signaturas de miembro|
|[CA1007](../code-quality/ca1007.md)|Utilizar valores genéricos cuando sea posible|
|[CA1008](../code-quality/ca1008.md)|Las enumeraciones deben tener un valor igual a cero|
|[CA1009](../code-quality/ca1009.md)|Declarar los controladores de evento correctamente|
|[CA1010](../code-quality/ca1010.md)|Las colecciones deben implementar la interfaz genérica|
|[CA1011](../code-quality/ca1011.md)|Considerar pasar los tipos base como parámetros|
|[CA1012](../code-quality/ca1012.md)|Los tipos abstractos no deberían tener constructores|
|[CA1013](../code-quality/ca1013.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1014](../code-quality/ca1014.md)|Marcar los ensamblados con CLSCompliantAttribute|
|[CA1016](../code-quality/ca1016.md)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1017](../code-quality/ca1017.md)|Marcar los ensamblados con ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|Marcar atributos con AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019.md)|Definir descriptores de acceso para los argumentos de atributo|
|[CA1023](../code-quality/ca1023.md)|Los indizadores no deben ser multidimensionales|
|[CA1024](../code-quality/ca1024.md)|Utilizar las propiedades donde corresponda|
|[CA1025](../code-quality/ca1025.md)|Reemplazar argumentos repetitivos por una matriz de parámetros|
|[CA1026](../code-quality/ca1026.md)|No deben usarse parámetros predeterminados|
|[CA1027](../code-quality/ca1027.md)|Marcar enumeraciones con FlagsAttribute|
|[CA1028](../code-quality/ca1028.md)|El almacenamiento de la enumeración debe ser de tipo Int32|
|[CA1030](../code-quality/ca1030.md)|Utilizar eventos cuando sea apropiado|
|[CA1031](../code-quality/ca1031.md)|No capturar los tipos de excepción general|
|[CA1032](../code-quality/ca1032.md)|Implementar constructores de excepción estándar|
|[CA1033](../code-quality/ca1033.md)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1034](../code-quality/ca1034.md)|Los tipos anidados no deben ser visibles|
|[CA1035](../code-quality/ca1035.md)|Las implementaciones de ICollection tienen miembros fuertemente tipados|
|[CA1036](../code-quality/ca1036.md)|Invalidar métodos en tipos comparables|
|[CA1038](../code-quality/ca1038.md)|Los enumeradores deben estar fuertemente tipados|
|[CA1039](../code-quality/ca1039.md)|Las listas están fuertemente tipadas|
|[CA1041](../code-quality/ca1041.md)|Proporcionar un mensaje ObsoleteAttribute|
|[CA1043](../code-quality/ca1043.md)|Utilizar un argumento integral o de cadena en indizadores|
|[CA1044](../code-quality/ca1044.md)|Las propiedades no deben ser de solo escritura|
|[CA1046](../code-quality/ca1046.md)|No sobrecargar el operador de igualdad en los tipos de referencia|
|[CA1047](../code-quality/ca1047.md)|No declarar miembros protegidos en tipos sellados|
|[CA1048](../code-quality/ca1048.md)|No declarar miembros virtuales en tipos sellados|
|[CA1049](../code-quality/ca1049.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1050](../code-quality/ca1050.md)|Declarar tipos en espacios de nombres|
|[CA1051](../code-quality/ca1051.md)|No declarar campos de instancia visibles|
|[CA1052](../code-quality/ca1052.md)|Los tipos titulares estáticos deben estar sellados|
|[CA1053](../code-quality/ca1053.md)|Los tipos titulares estáticos no deben tener constructores|
|[CA1054](../code-quality/ca1054.md)|Los parámetros de URI no deben ser cadenas|
|[CA1055](../code-quality/ca1055.md)|Los valores devueltos URI no deben ser cadenas|
|[CA1056](../code-quality/ca1056.md)|Las propiedades URI no deben ser cadenas|
|[CA1057](../code-quality/ca1057.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|
|[CA1058](../code-quality/ca1058.md)|Los tipos no deben ampliar ciertos tipos base|
|[CA1059](../code-quality/ca1059.md)|Los miembros no deben exponer algunos tipos concretos|
|[CA1060](../code-quality/ca1060.md)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](../code-quality/ca1061.md)|No ocultar métodos de clase base|
|[CA1063](../code-quality/ca1063.md)|Implementar IDisposable correctamente|
|[CA1064](../code-quality/ca1064.md)|Las excepciones deben ser públicas|
|[CA1065](../code-quality/ca1065.md)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401.md)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415.md)|Declarar elementos P/Invoke correctamente|
|[CA1500](../code-quality/ca1500.md)|Los nombres de las variables no deben coincidir con los nombres de los campos|
|[CA1502](../code-quality/ca1502.md)|Evitar una complejidad excesiva|
|[CA1708](../code-quality/ca1708.md)|Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas|
|[CA1716](../code-quality/ca1716.md)|Los identificadores no deben coincidir con palabras clave|
|[CA1801](../code-quality/ca1801.md)|Revisar parámetros sin utilizar|
|[CA1804](../code-quality/ca1804.md)|Quitar variables locales no utilizadas|
|[CA1809](../code-quality/ca1809.md)|Evitar las variables locales excesivas|
|[CA1810](../code-quality/ca1810.md)|Inicializar campos estáticos de tipo de referencia insertados|
|[CA1811](../code-quality/ca1811.md)|Evitar código privado al que no se llama|
|[CA1812](../code-quality/ca1812.md)|Evitar las clases internas sin instancia|
|[CA1813](../code-quality/ca1813.md)|Evitar los atributos no sellados|
|[CA1814](../code-quality/ca1814.md)|Preferir matrices escalonadas antes que multidimensionales|
|[CA1815](../code-quality/ca1815.md)|Invalidar Equals y el operador Equals en los tipos de valores|
|[CA1819](../code-quality/ca1819.md)|Las propiedades no deben devolver matrices|
|[CA1820](../code-quality/ca1820.md)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1821](../code-quality/ca1821.md)|Quitar finalizadores vacíos|
|[CA1822](../code-quality/ca1822.md)|Marcar miembros como estáticos|
|[CA1823](../code-quality/ca1823.md)|Evitar los campos privados sin utilizar|
|[CA1900](../code-quality/ca1900.md)|Los campos de tipo de valor deben ser portátiles|
|[CA1901](../code-quality/ca1901.md)|Las declaraciones P/Invoke deben ser portátiles|
|[CA2002](../code-quality/ca2002.md)|No bloquear objetos con identidad débil|
|[CA2100](../code-quality/ca2100.md)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2101](../code-quality/ca2101.md)|Especificar serialización en argumentos de cadena P/Invoke|
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
|[CA2200](../code-quality/ca2200.md)|Reiniciar para mantener los detalles de la pila|
|[CA2201](../code-quality/ca2201.md)|No provocar tipos de excepción reservados|
|[CA2202](../code-quality/ca2202.md)|No usar Dispose varias veces en objetos|
|[CA2205](../code-quality/ca2205.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2207](../code-quality/ca2207.md)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2208](../code-quality/ca2208.md)|Crear instancias de las excepciones del argumento correctamente|
|[CA2211](../code-quality/ca2211.md)|Los campos no constantes no deben ser visibles|
|[CA2212](../code-quality/ca2212.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](../code-quality/ca2213.md)|Los campos descartables deben ser descartables|
|[CA2214](../code-quality/ca2214.md)|No llamar a métodos reemplazables en constructores|
|[CA2216](../code-quality/ca2216.md)|Los tipos descartables deben declarar el finalizador|
|[CA2217](../code-quality/ca2217.md)|No marcar enumeraciones con FlagsAttribute|
|[CA2219](../code-quality/ca2219.md)|No producir excepciones en cláusulas de excepción|
|[CA2220](../code-quality/ca2220.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2221](../code-quality/ca2221.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2225](../code-quality/ca2225.md)|Las sobrecargas del operador tienen alternativas con nombre|
|[CA2226](../code-quality/ca2226.md)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Las propiedades de la colección deben ser de solo lectura|
|[CA2229](../code-quality/ca2229.md)|Implementar constructores de serialización|
|[CA2230](../code-quality/ca2230.md)|Usar parámetros en argumentos de variable|
|[CA2231](../code-quality/ca2231.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2234](../code-quality/ca2234.md)|Pasar objetos System.Uri en lugar de cadenas|
|[CA2235](../code-quality/ca2235.md)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialización correctamente|
|[CA2239](../code-quality/ca2239.md)|Proporcionar métodos de deserialización para campos opcionales|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable correctamente|
|[CA2241](../code-quality/ca2241.md)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](../code-quality/ca2242.md)|Comprobar NaN correctamente|
