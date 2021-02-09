---
title: Conjunto de reglas Reglas de seguridad para código administrado
ms.date: 11/04/2016
description: Obtenga información sobre el conjunto de reglas reglas de seguridad para el análisis de código heredado de Visual Studio. Vea descripciones de reglas que se centran en posibles problemas de seguridad.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2568137d5724613b0f5ddf801df6302c85e430f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859689"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas de seguridad para código administrado

Utilice el conjunto de reglas reglas de seguridad de Microsoft para el análisis de código heredado con el fin de maximizar el número de posibles problemas de seguridad que se muestran.

|Regla|Descripción|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2102](../code-quality/ca2102.md)|Detectar las excepciones que no son CLSCompliant en los controladores generales|
|[CA2103](../code-quality/ca2103.md)|Revisar la seguridad imperativa|
|[CA2104](../code-quality/ca2104.md)|No declarar tipos de referencias mutables de solo lectura|
|[CA2105](../code-quality/ca2105.md)|Los campos de matrices no deben ser de solo lectura|
|[CA2106](../code-quality/ca2106.md)|Proteger las aserciones|
|[CA2107](../code-quality/ca2107.md)|Revisar el uso de Deny y PermitOnly|
|[CA2108](../code-quality/ca2108.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Revisar los controladores de eventos visibles|
|[CA2111](../code-quality/ca2111.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2115](../code-quality/ca2115.md)|Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos|
|[CA2116](../code-quality/ca2116.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2118](../code-quality/ca2118.md)|Revisar el uso de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Sellar los métodos que satisfacen las interfaces privadas|
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
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|No usar el deserializador no seguro BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|No llamar a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Asegurarse de que BinaryFormatter.Binder está establecido antes de llamar a BinaryFormatter.Deserialize|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|No usar el deserializador no seguro LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|No usar el deserializador no seguro NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|No deserializar sin establecer primero NetDataContractSerializer.Binder|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|No usar el deserializador no seguro ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|No deserializar con JavaScriptSerializer mediante SimpleTypeResolver|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Asegúrese de que JavaScriptSerializer no se ha inicializado con SimpleTypeResolver antes de deserializar|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Revisión de código en busca de vulnerabilidades de inyección de SQL|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Revisión de código en busca de vulnerabilidades de XSS|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Revisión de código en busca de vulnerabilidades de divulgación de información|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Revisión de código en busca de vulnerabilidades de inyección de LDAP|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Revisión de código en busca de vulnerabilidades de redireccionamiento abierto|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Revisión de código en busca de vulnerabilidades de inyección de XPath|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Revisión de código en busca de vulnerabilidades de inyección de XML|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Revisión de código en busca de vulnerabilidades de inyección de XAML|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Revisión de código en busca de vulnerabilidades de inyección de DLL|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Revisión de código en busca de vulnerabilidades de inyección de expresiones regulares|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|No usar modos de cifrado inseguro|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|No codificar el certificado de forma rígida|