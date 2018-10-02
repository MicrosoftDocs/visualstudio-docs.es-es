---
title: 'CA2004: Quitar las llamadas a GC. KeepAlive | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8fbaa0bae44b09cef1d75c31c342ac6cf3e463df
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591133"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2004: quitar las llamadas a GC. KeepAlive](https://docs.microsoft.com/visualstudio/code-quality/ca2004-remove-calls-to-gc-keepalive).

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|Identificador de comprobación|CA2004|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Clases utilizan `SafeHandle` pero sigue sin contener las llamadas a `GC.KeepAlive`.

## <a name="rule-description"></a>Descripción de la regla
 Si va a convertir a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (objeto). En este caso, las clases no debe llamar a `GC.KeepAlive`, suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador del sistema operativo para ellos.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante con relación al rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para solucionar el problema que puedan existir ya no hace que el código sea más difícil de un período de duración mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite las llamadas a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir esta advertencia solo si no es técnicamente correcta convertir a `SafeHandle` uso en la clase.



