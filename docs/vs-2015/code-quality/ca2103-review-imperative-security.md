---
title: 'CA2103: Revisar la seguridad imperativa | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b8b3067d5c8ab8204d6ad723315c400e7b27552
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694925"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Revisar la seguridad imperativa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|Identificador de comprobación|CA2103|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa.

## <a name="rule-description"></a>Descripción de la regla
 Seguridad imperativa utiliza objetos administrados para especificar los permisos y las acciones de seguridad durante la ejecución de código, en comparación con la seguridad declarativa, que utiliza los atributos para almacenar los permisos y las acciones en los metadatos. La seguridad imperativa es muy flexible, ya que puede establecer el estado de un objeto de permiso y seleccionar acciones de seguridad mediante la información que no está disponible en tiempo de ejecución. Flexibilidad junto con la que produce el riesgo de que la información en tiempo de ejecución que se utiliza para determinar que el estado de un permiso no permanecen sin cambios siempre y cuando la acción está en vigor.

 Utilice la seguridad declarativa siempre que sea posible. Las demandas declarativas son más fáciles de entender.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise las demandas de seguridad imperativa para asegurarse de que el estado del permiso no se basa en información que puede cambiar mientras se está usando el permiso.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el permiso no se basa en datos que cambian. Sin embargo, es mejor cambiar la petición imperativa a su equivalente declarativo.

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
