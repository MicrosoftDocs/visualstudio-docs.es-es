---
description: Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener .NET Framework versión 4.
title: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 31ae6b1c4a80f7d28cdbbdd2c4d944cddf15227d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146956"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener .NET Framework versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de .NET Framework.

### <a name="to-correct-this-error"></a>Para corregir este error

- Realice uno de estos pasos:

  - Actualice .NET Framework a la versión 4.

  - Compile una versión de 32 bits de su aplicación para la depuración.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)
