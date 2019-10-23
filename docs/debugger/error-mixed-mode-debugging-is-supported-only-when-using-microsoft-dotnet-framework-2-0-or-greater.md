---
title: 'Error: solo se admite la depuración en modo mixto cuando se usa Microsoft .NET Framework 2,0 o superior | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: c85dac85146c59d8aeba9f9cf85351b5bc17a81c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737609"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Error: El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 o superior
Para depurar código nativo y administrado mixto, debe tener .NET Framework versión 2,0, 3,0. 3.5 ó 4. No se admite la depuración en modo mixto con versiones anteriores del .NET Framework.

### <a name="to-correct-this-error"></a>Para corregir este error

- Actualice el .NET Framework a la versión 2,0, 3,0, 3,5 o 4,0.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)