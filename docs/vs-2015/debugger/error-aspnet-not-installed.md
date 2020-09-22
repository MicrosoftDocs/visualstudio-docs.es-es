---
title: 'Error: ASP.NET no está instalado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843098"
---
# <a name="error-aspnet-not-installed"></a>Error: ASP.NET no está instalado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error se produce si [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no está correctamente instalado en el equipo en el que intenta depurar. Esto puede significar que nunca se instaló [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o que se instaló [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] antes que IIS.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar ASP.NET  
  
1. Desde una ventana del símbolo del sistema, ejecute el siguiente comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     Donde *version* representa el número de la versión de .NET Framework instalada en el equipo, por ejemplo, la 1.0.370. Para determinar la versión de .NET Framework, consulte el directorio `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    > En Windows Server 2003, puede instalar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] mediante el subprograma **Agregar o quitar programas** del Panel de control.  
  
## <a name="see-also"></a>Consulte también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
