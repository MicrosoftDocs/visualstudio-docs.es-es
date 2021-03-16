---
description: Este error se produce si ASP.NET no está correctamente instalado en el equipo en el que intenta depurar.
title: ASP.NET no está instalado
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 205f0fb3948414ec87b735af9b1b97917872a950
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147060"
---
# <a name="error-aspnet-not-installed"></a>Error: ASP.NET no está instalado
Este error se produce si [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no está correctamente instalado en el equipo en el que intenta depurar. Esto puede significar que nunca se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o que se instaló [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] antes que IIS.

### <a name="to-reinstall-aspnet"></a>Para reinstalar ASP.NET

1. Desde una ventana del símbolo del sistema, ejecute el siguiente comando:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    Donde *version* representa el número de la versión de .NET Framework instalada en el equipo, por ejemplo, la 1.0.370. Para determinar la versión de .NET Framework, consulte el directorio `\WINDOWS\Microsoft.NET\Framework`.

   > [!NOTE]
   > En Windows Server 2003, puede instalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el subprograma **Agregar o quitar programas** del Panel de control.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
