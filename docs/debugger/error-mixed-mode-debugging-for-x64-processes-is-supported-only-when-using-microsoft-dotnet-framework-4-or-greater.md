---
title: 'Error: Modo mixto de depuración para x64 procesos solo se admite cuando usa Microsoft .NET Framework 4 o mayor | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745433"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener .NET Framework versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con las versiones de .NET Framework anteriores a 4.

### <a name="to-correct-this-error"></a>Para corregir este error

- Realice uno de estos pasos:

  - Actualice su entorno .NET Framework a la versión 4.

  - Compile una versión de 32 bits de su aplicación para la depuración.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)