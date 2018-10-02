---
title: 'Error: El modo mixto depuración para x64 procesos solo se admite cuando usa Microsoft .NET Framework 4 o mayor | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 479a771300e37e09412accb16771d31454469f95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574645"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Error: El modo de depuración mixto para procesos x64 se admite sólo cuando se usa Microsoft .NET Framework 4 o posterior
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: modo mixto de depuración para x64 procesos solo se admite cuando usa Microsoft .NET Framework 4 o mayor](https://docs.microsoft.com/visualstudio/debugger/error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-dotnet-framework-4-or-greater).  
  
Para depurar código nativo y administrado mixto en un proceso de 64 bits, debe tener [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versión 4. No se admite la depuración en modo mixto de procesos de 64 bits con versiones anteriores a la 4 de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Realice uno de estos pasos:  
  
    -   Actualice [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a la versión 4.  
  
    -   Compile una versión de 32 bits de su aplicación para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Configurar las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



