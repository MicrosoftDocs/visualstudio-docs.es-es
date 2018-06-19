---
title: 'Error: Mixto-modo de depuración para x64 procesos se admite solo cuando se usa Microsoft .NET Framework 4 o mayor | Documentos de Microsoft'
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
ms.openlocfilehash: d5550383d1d5882d8824ce2d282b2035882cdcef
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471510"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite sólo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Realice uno de estos pasos:  
  
    -   Actualice [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la versión 4.  
  
    -   Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)