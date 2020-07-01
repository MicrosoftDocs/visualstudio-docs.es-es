---
title: 'CA2103: revisar la seguridad imperativa | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ade0d10e203752c7412929c6f5f44d9cbfaacfa6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521269"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Revisar la seguridad imperativa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|ReviewImperativeSecurity|
|Identificador de comprobación|CA2103|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa.

## <a name="rule-description"></a>Descripción de la regla
 La seguridad imperativa utiliza objetos administrados para especificar permisos y acciones de seguridad durante la ejecución del código, en comparación con la seguridad declarativa, que utiliza atributos para almacenar permisos y acciones en los metadatos. La seguridad imperativa es muy flexible, ya que puede establecer el estado de un objeto de permiso y seleccionar acciones de seguridad mediante la información que no está disponible hasta el tiempo de ejecución. Junto con esa flexibilidad, existe el riesgo de que la información en tiempo de ejecución que se usa para determinar el estado de un permiso no se modifique, siempre y cuando la acción esté en vigor.

 Utilice la seguridad declarativa siempre que sea posible. Las peticiones declarativas son más fáciles de entender.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise las demandas de seguridad imperativa para asegurarse de que el estado del permiso no se basa en la información que puede cambiar siempre que se use el permiso.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el permiso no depende de los datos modificados. Sin embargo, es mejor cambiar la demanda imperativa a su equivalente declarativo.

## <a name="see-also"></a>Consulte también
 [Modelos de datos y modelado de instrucciones de](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
