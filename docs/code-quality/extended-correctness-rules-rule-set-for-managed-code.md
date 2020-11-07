---
title: Conjunto de reglas Reglas de corrección extendidas para código administrado
ms.date: 11/04/2016
description: Obtenga información sobre el conjunto de reglas reglas de corrección extendidas en Visual Studio, que es útil para la interoperabilidad COM y las aplicaciones móviles. Vea las descripciones de las reglas.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6aa97d246ac767cc3c88c845298e2db61edcd35f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349001"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de corrección extendidas para código administrado

El conjunto de reglas reglas de corrección extendidas de Microsoft maximiza los errores de uso de la lógica y el marco de trabajo que se indican en el análisis de código. Se pone especial énfasis en escenarios específicos como la interoperabilidad COM y las aplicaciones móviles. Debe considerar la posibilidad de incluir este conjunto de reglas si alguno de estos escenarios se aplica a su proyecto o para buscar problemas adicionales en el proyecto.

El conjunto de reglas reglas de corrección extendidas de Microsoft incluye las reglas que se encuentran en el conjunto de reglas [reglas de corrección básicas](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , que contiene las reglas que se encuentran en el conjunto de reglas [reglas recomendadas administradas](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

En la tabla siguiente se describen todas las reglas del conjunto de reglas reglas de corrección extendidas de Microsoft.

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
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Las enumeraciones deben tener un valor igual a cero|
|[CA1013](../code-quality/ca1013.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|No pasar literales como parámetros localizados|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizar cadenas en mayúsculas|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|No omitir resultados del método|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Llamar a GC.SuppressFinalize correctamente|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Las propiedades no deben devolver matrices|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1903](../code-quality/ca1903.md)|Usar solo API de la versión de .NET Framework de destino|
|[CA2004](../code-quality/ca2004.md)|Quitar las llamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Utilizar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2104](../code-quality/ca2104.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105.md)|Los campos de matrices no deben ser de solo lectura|
|[CA2106](../code-quality/ca2106.md)|Proteger las aserciones|
|[CA2115](../code-quality/ca2115.md)|Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Sellar los métodos que satisfacen las interfaces privadas|
|[CA2120](../code-quality/ca2120.md)|Proteger los constructores de serializaciones|
|[CA2121](../code-quality/ca2121.md)|Los constructores estáticos deben ser privados|
|[CA2130](../code-quality/ca2130.md)|Las constantes críticas para la seguridad deben ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Los métodos Dispose deben llamar al método Dispose de la clase base|
|[CA2221](../code-quality/ca2221.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Las propiedades de la colección deben ser de solo lectura|
|[CA2239](../code-quality/ca2239.md)|Proporcionar métodos de deserialización para campos opcionales|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implementar constructores de excepción estándar|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Los parámetros de URI no deben ser cadenas|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Los valores devueltos URI no deben ser cadenas|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Las propiedades URI no deben ser cadenas|
|[CA1057](../code-quality/ca1057.md)|Las sobrecargas URI de cadena llaman a sobrecargas System.Uri|
|[CA1402](../code-quality/ca1402.md)|Evitar las sobrecargas en interfaces visibles a través de COM|
|[CA1406](../code-quality/ca1406.md)|Evitar los argumentos Int64 en clientes Visual Basic 6|
|[CA1407](../code-quality/ca1407.md)|Evitar los miembros estáticos en tipos visibles a través de COM|
|[CA1408](../code-quality/ca1408.md)|No utilizar AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409.md)|Los tipos visibles a través de COM se deben poder crear|
|[CA1411](../code-quality/ca1411.md)|Los métodos de registro COM no deben ser visibles|
|[CA1412](../code-quality/ca1412.md)|Marcar las interfaces ComSource como IDispatch|
|[CA1413](../code-quality/ca1413.md)|Evitar los campos no públicos en tipos de valor visibles a través de COM|
|[CA1414](../code-quality/ca1414.md)|Marcar los argumentos P/Invoke booleanos con MarshalAs|
|[CA1600](../code-quality/ca1600.md)|No utilizar la prioridad del proceso inactiva|
|[CA1601](../code-quality/ca1601.md)|No utilizar temporizadores que impidan los cambios de estado de energía|
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Marcar los ensamblados con NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Evitar llamar a métodos problemáticos|
|[CA2003](../code-quality/ca2003.md)|No tratar fibras como subprocesos|
|[CA2135](../code-quality/ca2135.md)|Los ensamblados de nivel 2 no deben contener LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Los miembros no deben tener anotaciones de transparencia en conflicto|
|[CA2139](../code-quality/ca2139.md)|Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|El código transparente no debe protegerse con LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Los métodos transparentes no deben usar peticiones de seguridad|
|[CA2144](../code-quality/ca2144.md)|El código transparente no debe cargar ensamblados desde matrices de bytes|
|[CA2145](../code-quality/ca2145.md)|Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Los literales deben estar escritos correctamente|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Los campos no constantes no deben ser visibles|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|No marcar enumeraciones con FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Invalidar el método GetHashCode al invalidar el método Equals|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|No producir excepciones en cláusulas de excepción|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Las sobrecargas del operador tienen alternativas con nombre|
|[CA2228](../code-quality/ca2228.md)|No enviar formatos de recursos no lanzados|
|[CA2230](../code-quality/ca2230.md)|Usar parámetros en argumentos de variable|
|[CA2233](../code-quality/ca2233.md)|Las operaciones no deben desbordarse|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Pasar objetos System.Uri en lugar de cadenas|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Los literales de cadena de atributo se deben analizar correctamente|
