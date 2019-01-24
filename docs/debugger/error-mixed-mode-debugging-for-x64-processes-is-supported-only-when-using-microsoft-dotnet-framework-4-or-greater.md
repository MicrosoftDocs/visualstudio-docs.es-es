---
title: 'Error: Modo mixto de depuración para x64 procesos solo se admite cuando usa Microsoft .NET Framework 4 o mayor | Microsoft Docs'
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4098689338d0c0c647964e4d13e59ab860e42e4c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827409"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Realice uno de estos pasos:  
  
  - Actualice [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la versión 4.  
  
  - Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Remote Debugging](../debugger/remote-debugging.md)