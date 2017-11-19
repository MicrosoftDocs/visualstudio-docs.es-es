---
title: "Error: Mixto-modo de depuración para x64 procesos se admite solo cuando se usa Microsoft .NET Framework 4 o mayor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80487995064f01c61e21e067e92b9fb5eb0c53f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite sólo cuando se usa Microsoft .NET Framework 4 o posterior
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Realice uno de estos pasos:  
  
    -   Actualice [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la versión 4.  
  
    -   Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)