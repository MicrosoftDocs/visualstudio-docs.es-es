---
title: advertencias de confiabilidad
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c690be59758ca17a573d742fc0f75c81b955d5ad
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916753"
---
# <a name="reliability-warnings"></a>advertencias de confiabilidad
Advertencias de confiabilidad admiten la confiabilidad de bibliotecas y aplicaciones, como el uso de memoria y el subproceso correcto.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA2000: Desechar (Dispose) objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|
|[CA2001: Evitar llamar a métodos problemáticos](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un miembro llama a un método potencialmente peligroso o problemático.|
|[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|
|[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un subproceso administrado se trata como un subproceso de Win32.|
|[CA2004: Quitar las llamadas a GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Si va a convertir para utilizar SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no deben tener que llamar a GC. KeepAlive, suponiendo que no tienen un finalizador sino que dependen de SafeHandle para finalizar el sistema operativo controlarán por ellos.|
|[CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|