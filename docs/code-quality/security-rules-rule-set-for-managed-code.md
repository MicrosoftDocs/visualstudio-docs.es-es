---
title: Conjunto de reglas Reglas de seguridad para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ea23186ff03ccdb0ff7678380eadc866b63654f2
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918913"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de seguridad para código administrado

Utilice el conjunto de reglas reglas de seguridad de Microsoft para el análisis de código heredado con el fin de maximizar el número de posibles problemas de seguridad que se muestran.

|Regla|Descripción|
|----------|-----------------|
|[CA2100](../code-quality/ca2100.md)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2102](../code-quality/ca2102.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2103](../code-quality/ca2103.md)|Revisar la seguridad imperativa|
|[CA2104](../code-quality/ca2104.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105.md)|Los campos de matrices no deben ser de solo lectura|
|[CA2106](../code-quality/ca2106.md)|Proteger las aserciones|
|[CA2107](../code-quality/ca2107.md)|Revisar el uso de Deny y PermitOnly|
|[CA2108](../code-quality/ca2108.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2109](../code-quality/ca2109.md)|Revisar los controladores de eventos visibles|
|[CA2111](../code-quality/ca2111.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2115](../code-quality/ca2115.md)|Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos|
|[CA2116](../code-quality/ca2116.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2118](../code-quality/ca2118.md)|Revisar el uso de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119.md)|Sellar los métodos que satisfacen las interfaces privadas|
|[CA2120](../code-quality/ca2120.md)|Proteger los constructores de serializaciones|
|[CA2121](../code-quality/ca2121.md)|Los constructores estáticos deben ser privados|
|[CA2122](../code-quality/ca2122.md)|No exponer indirectamente métodos con peticiones de vínculos|
|[CA2123](../code-quality/ca2123.md)|Las peticiones de vínculos de invalidaciones deben ser idénticas a la base|
|[CA2124](../code-quality/ca2124.md)|Incluir cláusulas finally vulnerables en un bloque try externo|
|[CA2126](../code-quality/ca2126.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2130](../code-quality/ca2130.md)|Las constantes críticas para la seguridad deben ser transparentes|
|[CA2131](../code-quality/ca2131.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base|
|[CA2133](../code-quality/ca2133.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134.md)|Los métodos deben mantener una transparencia coherente al invalidar métodos base|
|[CA2135](../code-quality/ca2135.md)|Los ensamblados de nivel 2 no deben contener LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Los miembros no deben tener anotaciones de transparencia en conflicto|
|[CA2137](../code-quality/ca2137.md)|Los métodos transparentes deben contener solo IL que se pueda comprobar|
|[CA2138](../code-quality/ca2138.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141.md)|Los métodos transparentes no deben satisfacer LinkDemands|
|[CA2142](../code-quality/ca2142.md)|El código transparente no debe protegerse con LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Los métodos transparentes no deben usar peticiones de seguridad|
|[CA2144](../code-quality/ca2144.md)|El código transparente no debe cargar ensamblados desde matrices de bytes|
|[CA2145](../code-quality/ca2145.md)|Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base|
|[CA2147](../code-quality/ca2147.md)|Los métodos transparentes no pueden usar aserciones de seguridad|
|[CA2149](../code-quality/ca2149.md)|Los métodos transparentes no deben llamar a código nativo|
|[CA2210](../code-quality/ca2210.md)|Los ensamblados deben tener nombres seguros válidos|
|[CA2300](ca2300.md)|No usar el deserializador no seguro BinaryFormatter|
|[CA2301](ca2301.md)|No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder|
|[CA2302](ca2302.md)|Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize|
|[CA2305](ca2305.md)|No usar el deserializador no seguro LosFormatter|
|[CA2310](ca2310.md)|No usar el deserializador no seguro NetDataContractSerializer|
|[CA2311](ca2311.md)|No deserializar sin establecer primero NetDataContractSerializer.Binder|
|[CA2312](ca2312.md)|Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar|
|[CA2315](ca2315.md)|No usar el deserializador no seguro ObjectStateFormatter|
|[CA2321](ca2321.md)|No deserializar con JavaScriptSerializer mediante SimpleTypeResolver|
|[CA2322](ca2322.md)|Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar|
|[CA3001](../code-quality/ca3001.md)|Revisión de código en busca de vulnerabilidades de inyección de SQL|
|[CA3002](../code-quality/ca3002.md)|Revisión de código en busca de vulnerabilidades de XSS|
|[CA3003](../code-quality/ca3003.md)|Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos|
|[CA3004](../code-quality/ca3004.md)|Revisión de código en busca de vulnerabilidades de divulgación de información|
|[CA3005](../code-quality/ca3005.md)|Revisión de código en busca de vulnerabilidades de inyección de LDAP|
|[CA3006](../code-quality/ca3006.md)|Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos|
|[CA3007](../code-quality/ca3007.md)|Revisión de código en busca de vulnerabilidades de redireccionamiento abierto|
|[CA3008](../code-quality/ca3008.md)|Revisión de código en busca de vulnerabilidades de inyección de XPath|
|[CA3009](../code-quality/ca3009.md)|Revisión de código en busca de vulnerabilidades de inyección de XML|
|[CA3010](../code-quality/ca3010.md)|Revisión de código en busca de vulnerabilidades de inyección de XAML|
|[CA3011](../code-quality/ca3011.md)|Revisión de código en busca de vulnerabilidades de inyección de DLL|
|[CA3012](../code-quality/ca3012.md)|Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares|
|[CA5403](../code-quality/ca5403.md)|No codificar certificado de forma rígida|
