---
title: 'Error: Depuración en modo mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 o superior | Documentos de Microsoft'
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850682"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Error: El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 o superior
Para depurar código nativo y administrado, debe tener la versión 2.0, 3.0 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. 3.5 ó 4. No se admite la depuración en modo mixto con versiones anteriores de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

### <a name="to-correct-this-error"></a>Para corregir este error

- Actualice [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la versión 2.0, 3.0, 3.5 o 4.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)