---
title: 'CA2003: No tratar fibras como subprocesos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8faaf3c6557065188c795d75ea9bbe4e78998709
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806993"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: No tratar fibras como subprocesos

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|Identificador de comprobación|CA2003|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un subproceso administrado se trata como un subproceso de Win32.

## <a name="rule-description"></a>Descripción de la regla

No suponga que un subproceso administrado es un subproceso de Win32; es una fibra. Common language runtime (CLR) ejecuta subprocesos administrados como fibras en el contexto de subprocesos reales que pertenecen a SQL. Estos subprocesos se pueden compartir entre dominios de aplicación y las bases de datos incluso en el proceso de SQL Server. Mediante administrado funciona de almacenamiento local de subproceso, pero no se puede utilizar almacenamiento local de subprocesos no administrados ni suponer que el código se ejecutará en el subproceso del sistema operativo actual de nuevo. No cambie la configuración, como la configuración regional del subproceso. No llame a CreateCriticalSection o CreateMutex a través de P/Invoke porque requieren que el subproceso que entra en un bloqueo también salga el bloqueo. Dado que el subproceso que entra en un bloqueo no cierre un bloqueo cuando se utilizan fibras, secciones críticas de Win32 y las exclusiones mutuas son inútiles en SQL. Puede usar sin ningún riesgo la mayor parte del estado en administrado <xref:System.Threading.Thread> objeto, incluido el almacenamiento local de subprocesos administrados y la referencia cultural actual (UI) de la interfaz de usuario del subproceso. Sin embargo, para motivos del modelo de programación, no podrá cambiar la referencia cultural actual de un subproceso al usar SQL. Esta limitación se aplicarán a través de un nuevo permiso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Examine el uso de subprocesos y cambiar el código en consecuencia.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima esta regla.