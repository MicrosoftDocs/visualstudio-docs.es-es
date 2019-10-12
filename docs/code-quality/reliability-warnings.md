---
title: advertencias de confiabilidad
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252589"
---
# <a name="reliability-warnings"></a>Advertencias de confiabilidad

Las advertencias de confiabilidad admiten la confiabilidad de bibliotecas y aplicaciones, como la memoria y el uso de subprocesos correctos. Las reglas de confiabilidad incluyen:

|Regla|Descripción|
|----------|-----------------|
|@NO__T 0CA2000: Desechar objetos antes de perder el ámbito @ no__t-0|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|
|@NO__T 0CA2001: Evitar llamar a métodos problemáticos @ no__t-0|Un miembro llama a un método potencialmente peligroso o problemático.|
|[CA2002: No bloquear objetos con identidad débil @ no__t-0|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|
|@NO__T 0CA2003: No tratar fibras como subprocesos @ no__t-0|Un subproceso administrado se trata como un subproceso de Win32.|
|@NO__T 0CA2004: Quite las llamadas a GC. KeepAlive @ no__t-0|Si va a realizar la conversión al uso de SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no deben tener que llamar a GC. KeepAlive, suponiendo que no tienen un finalizador, sino que se basan en SafeHandle para finalizar el identificador de sistema operativo.|
|@NO__T 0CA2006: Usar SafeHandle para encapsular recursos nativos @ no__t-0|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|
|@NO__T 0CA2007: No esperar directamente a una tarea @ no__t-0|Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directamente.|
