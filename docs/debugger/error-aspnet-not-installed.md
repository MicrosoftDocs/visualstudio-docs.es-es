---
title: 'Error: ASP.NET no instalado | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 41d2804ce3cab18acf697333ee9950b4717f9500
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="error-aspnet-not-installed"></a>Error: ASP.NET no está instalado
Este error se produce si [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no está correctamente instalado en el equipo en el que intenta depurar. Esto puede significar que nunca se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o que se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] antes que IIS.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar ASP.NET  
  
1.  Desde una ventana del símbolo del sistema, ejecute el siguiente comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     donde *versión* representa el número de versión de .NET Framework instalada en el equipo, por ejemplo, v1.0.370. Puede determinar la versión de framework mediante una búsqueda en el `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Con Windows Server 2003, puede instalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] utilizando **agregar o quitar programas** en el Panel de Control.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)