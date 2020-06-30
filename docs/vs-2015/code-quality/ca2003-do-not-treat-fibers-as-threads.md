---
title: 'CA2003: no tratar fibras como subprocesos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521179"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: No tratar fibras como subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|Identificador de comprobación|CA2003|
|Category|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un subproceso administrado se trata como un subproceso de Win32.

## <a name="rule-description"></a>Descripción de la regla
 No asuma que un subproceso administrado es un subproceso de Win32. Es una fibra. El Common Language Runtime (CLR) ejecutará los subprocesos administrados como fibras en el contexto de los subprocesos reales que son propiedad de SQL. Estos subprocesos se pueden compartir entre AppDomains e incluso las bases de datos del proceso de SQL Server. El uso de almacenamiento local de subprocesos administrados funcionará, pero es posible que no use el almacenamiento local de subprocesos no administrados ni asuma que el código se ejecutará de nuevo en el subproceso de sistema operativo actual. No cambie la configuración, como la configuración regional del subproceso. No llame a CreateCriticalSection o CreateMutex a través de P/Invoke porque requieren que el subproceso que entra en un bloqueo también debe salir del bloqueo. Dado que no es el caso cuando se usan fibras, las secciones críticas de Win32 y las exclusiones mutuas no serán útiles en SQL. Puede usar la mayor parte del estado en un objeto System. Thread administrado. Esto incluye el almacenamiento local de subprocesos administrados y la referencia cultural de la interfaz de usuario actual del subproceso. Sin embargo, para los motivos del modelo de programación, no podrá cambiar la referencia cultural actual de un subproceso cuando use SQL; Esto se aplicará a través de un nuevo permiso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Examine el uso de subprocesos y cambie el código en consecuencia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No debe suprimir esta regla.
