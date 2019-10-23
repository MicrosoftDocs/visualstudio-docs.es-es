---
title: Conjunto de reglas Reglas de corrección básicas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 53d17f51a777c4b39cd5ff8e0a444d1aec56583c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607710"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de corrección básicas para código administrado

El conjunto de reglas reglas de corrección básicas se centra en los errores de lógica y los errores comunes en el uso de las API de .NET Framework. Las reglas de corrección básicas incluyen las reglas del conjunto de reglas [reglas recomendadas administradas](managed-recommended-rules-rule-set-for-managed-code.md) .

En la tabla siguiente se describen todas las reglas del conjunto de reglas reglas de corrección básicas de Microsoft.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1009](../code-quality/ca1009.md)|Declarar los controladores de evento correctamente|
|[CA1016](../code-quality/ca1016.md)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1049](../code-quality/ca1049.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1060](../code-quality/ca1060.md)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](../code-quality/ca1061.md)|No ocultar métodos de clase base|
|[CA1063](../code-quality/ca1063.md)|Implementar IDisposable correctamente|
|[CA1065](../code-quality/ca1065.md)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401.md)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415.md)|Declarar elementos P/Invoke correctamente|
|[CA1821](../code-quality/ca1821.md)|Quitar finalizadores vacíos|
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
|[CA2202](../code-quality/ca2202.md)|No usar Dispose varias veces en objetos|
|[CA2207](../code-quality/ca2207.md)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](../code-quality/ca2213.md)|Los campos descartables deben ser descartables|
|[CA2214](../code-quality/ca2214.md)|No llamar a métodos reemplazables en constructores|
|[CA2216](../code-quality/ca2216.md)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](../code-quality/ca2229.md)|Implementar constructores de serialización|
|[CA2231](../code-quality/ca2231.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](../code-quality/ca2235.md)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable correctamente|
|[CA2241](../code-quality/ca2241.md)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](../code-quality/ca2242.md)|Comprobar NaN correctamente|
|[CA1008](../code-quality/ca1008.md)|Las enumeraciones deben tener un valor igual a cero|
|[CA1013](../code-quality/ca1013.md)|El operador de sobrecarga es igual que la suma y resta de sobrecarga|
|[CA1303](../code-quality/ca1303.md)|No pasar literales como parámetros localizados|
|[CA1308](../code-quality/ca1308.md)|Normalizar cadenas en mayúsculas|
|[CA1806](../code-quality/ca1806.md)|No omitir resultados del método|
|[CA1816](../code-quality/ca1816.md)|Llamar a GC.SuppressFinalize correctamente|
|[CA1819](../code-quality/ca1819.md)|Las propiedades no deben devolver matrices|
|[CA1820](../code-quality/ca1820.md)|Comprobar si las cadenas están vacías mediante la longitud de cadena|
|[CA1903](../code-quality/ca1903.md)|Usar solo API de la versión de .NET Framework de destino|
|[CA2004](../code-quality/ca2004.md)|Quitar las llamadas a GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Utilizar SafeHandle para encapsular recursos nativos|
|[CA2102](../code-quality/ca2102.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2104](../code-quality/ca2104.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105.md)|Los campos de matrices no deben ser de solo lectura|
|[CA2106](../code-quality/ca2106.md)|Proteger las aserciones|
|[CA2115](../code-quality/ca2115.md)|Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos|
|[CA2119](../code-quality/ca2119.md)|Sellar los métodos que satisfacen las interfaces privadas|
|[CA2120](../code-quality/ca2120.md)|Proteger los constructores de serializaciones|
|[CA2121](../code-quality/ca2121.md)|Los constructores estáticos deben ser privados|
|[CA2130](../code-quality/ca2130.md)|Las constantes críticas para la seguridad deben ser transparentes|
|[CA2205](../code-quality/ca2205.md)|Utilizar equivalentes administrados de la API Win32|
|[CA2215](../code-quality/ca2215.md)|Los métodos Dispose deben llamar al método Dispose de la clase base|
|[CA2221](../code-quality/ca2221.md)|Los finalizadores deben estar protegidos|
|[CA2222](../code-quality/ca2222.md)|No disminuir la visibilidad del miembro heredado|
|[CA2223](../code-quality/ca2223.md)|Los miembros deben diferenciarse por algo más que por un tipo de valor devuelto|
|[CA2224](../code-quality/ca2224.md)|Invalidar Equals al sobrecargar operadores de igualdad|
|[CA2226](../code-quality/ca2226.md)|Los operadores deben tener sobrecargas simétricas|
|[CA2227](../code-quality/ca2227.md)|Las propiedades de la colección deben ser de solo lectura|
|[CA2239](../code-quality/ca2239.md)|Proporcionar métodos de deserialización para campos opcionales|
