---
title: 'Error: El modo mixto depuración para x64 procesos solo se admite cuando usa Microsoft .NET Framework 4 o mayor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: b1e7159c67ab104156f2dccd6d89413594ded33c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874415"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite sólo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Realice uno de estos pasos:  
  
  - Actualice [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la versión 4.  
  
  - Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Remote Debugging](../debugger/remote-debugging.md)