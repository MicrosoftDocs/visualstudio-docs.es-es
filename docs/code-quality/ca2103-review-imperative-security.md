---
title: 'CA2103: Revisar la seguridad imperativa'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d107690e8835f118861832da99b4aef92e86a5cc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Revisar la seguridad imperativa
|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|Identificador de comprobación|CA2103|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa.

## <a name="rule-description"></a>Descripción de la regla
 La seguridad imperativa utiliza objetos administrados para especificar permisos y acciones de seguridad durante la ejecución de código, en comparación con la seguridad declarativa, que utiliza los atributos para almacenar permisos y acciones en los metadatos. La seguridad imperativa es muy flexible, ya que puede establecer el estado de un objeto de permiso y seleccionar las acciones de seguridad mediante la información que no está disponible en tiempo de ejecución. Flexibilidad junto con la que produce el riesgo de que la información en tiempo de ejecución que usa para determinar que el estado de un permiso no permanecen sin cambios siempre que la acción está en vigor.

 Utilice la seguridad declarativa siempre que sea posible. Las solicitudes declarativas son fáciles de entender.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise las solicitudes de seguridad imperativa para asegurarse de que el estado del permiso no se basa en información que puede cambiar mientras se está usando el permiso.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el permiso no se basa en datos que cambian. Sin embargo, es mejor cambiar la petición imperativa a su equivalente declarativo.

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines) [datos y modelado](/dotnet/framework/data/index)