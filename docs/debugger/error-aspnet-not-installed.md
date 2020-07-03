---
title: 'Error: ASP.NET no está instalado | Microsoft Docs'
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 3a768a1a3a0295190701cacc9bbf017baee507b7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460910"
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
