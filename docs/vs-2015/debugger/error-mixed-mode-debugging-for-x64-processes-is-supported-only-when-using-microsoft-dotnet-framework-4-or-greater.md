---
title: 'Error: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190a6e890ce31ce2aa66ff474bb9e4b1976a6c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824009"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite solo cuando se usa Microsoft .NET Framework 4 o posterior
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Realice uno de estos pasos:  
  
  - Actualice [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a la versión 4.  

  - Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Configurar las herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
