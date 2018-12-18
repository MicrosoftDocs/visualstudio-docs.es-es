---
title: 'CA2003: No tratar fibras como subprocesos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3d72e052decc5a26dd134aafcaac8aba6af699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810923"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: No tratar fibras como subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|Identificador de comprobación|CA2003|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un subproceso administrado se trata como un subproceso de Win32.

## <a name="rule-description"></a>Descripción de la regla
 No suponga que un subproceso administrado es un subproceso de Win32. Es una fibra. Common language runtime (CLR) ejecutará los subprocesos administrados como fibras en el contexto de subprocesos reales que pertenecen a SQL. Estos subprocesos se pueden compartir entre dominios de aplicación y las bases de datos incluso en el proceso de SQL Server. Mediante administrado funcionará el almacenamiento local de subproceso, pero no se puede utilizar almacenamiento local de subprocesos no administrados ni suponer que el código se ejecutará en el subproceso del sistema operativo actual de nuevo. No cambie la configuración, como la configuración regional del subproceso. No llame a CreateCriticalSection o CreateMutex a través de P/Invoke porque requieren que el subproceso que entra en un bloqueo también salga el bloqueo. Dado que este no es el caso cuando se utilizan fibras, secciones críticas de Win32 y las exclusiones mutuas será inútiles en SQL. Puede usar sin ningún riesgo la mayor parte del estado en mutuas. Esto incluye el almacenamiento local de subprocesos administrados y la referencia cultural actual (UI) de la interfaz de usuario del subproceso. Sin embargo, para motivos del modelo de programación, no podrá cambiar la referencia cultural actual de un subproceso cuando se usa SQL; Esto se aplicará a través de un nuevo permiso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Examine el uso de subprocesos y cambiar el código en consecuencia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No debe suprimir esta regla.



