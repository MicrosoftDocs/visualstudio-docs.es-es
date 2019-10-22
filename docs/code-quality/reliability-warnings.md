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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 602f372e11c4a9a8506186535958fc4f22da7806
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649114"
---
# <a name="reliability-warnings"></a>Advertencias de confiabilidad

Las advertencias de confiabilidad admiten la confiabilidad de bibliotecas y aplicaciones, como la memoria y el uso de subprocesos correctos. Las reglas de confiabilidad incluyen:

|Regla|Descripción|
|----------|-----------------|
|[CA2000: Desechar (Dispose) objetos antes de perder el ámbito](../code-quality/ca2000.md)|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|
|[CA2001: Evitar llamar a métodos problemáticos](../code-quality/ca2001.md)|Un miembro llama a un método potencialmente peligroso o problemático.|
|[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002.md)|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|
|[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003.md)|Un subproceso administrado se trata como un subproceso de Win32.|
|[CA2004: Quitar las llamadas a GC.KeepAlive](../code-quality/ca2004.md)|Si va a realizar la conversión al uso de SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no deben tener que llamar a GC. KeepAlive, suponiendo que no tienen un finalizador, sino que se basan en SafeHandle para finalizar el identificador de sistema operativo.|
|[CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006.md)|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|
|[CA2007: no espera directamente a una tarea](../code-quality/ca2007.md)|Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directamente.|
