---
title: 'CA2004: Quite las llamadas a GC. KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521204"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Quitar las llamadas a GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|Identificador de comprobación|CA2004|
|Category|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Las clases usan `SafeHandle` pero todavía contienen llamadas a `GC.KeepAlive` .

## <a name="rule-description"></a>Descripción de la regla
 Si está convirtiendo a `SafeHandle` uso, quite todas las llamadas a `GC.KeepAlive` (Object). En este caso, las clases no deben llamar a `GC.KeepAlive` , suponiendo que no tienen un finalizador sino que se basan en `SafeHandle` para completar el identificador del sistema operativo.  Aunque el costo de dejar en una llamada a `GC.KeepAlive` puede ser insignificante según lo medido por el rendimiento, la percepción de que una llamada a `GC.KeepAlive` es necesaria o suficiente para resolver un problema de duración que puede que ya no exista hace que el código sea más difícil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite las llamadas a `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir esta advertencia solo si no es técnicamente correcta para realizar la conversión al `SafeHandle` uso en la clase.
