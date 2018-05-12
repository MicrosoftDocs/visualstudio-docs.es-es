---
title: 'Error: El Microsoft Visual Studio Monitor de depuración remota en el equipo remoto no tiene permiso para conectarse a este equipo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 266a301bca4953066621d759518c1754052dfeb2
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse a este equipo.
Este error aparece cuando el usuario que intenta ejecutar el Monitor de depuración remota de Visual Studio (msvsmon) no tiene una cuenta en el equipo local.  
  
### <a name="to-fix-this-problem"></a>Para corregir este problema  
  
-   Agregue una cuenta de usuario al equipo host del depurador de Visual Studio, con el mismo nombre y contraseña que la cuenta de usuario que ejecuta msvsmon en el equipo remoto  
  
     \- o -  
  
-   Ejecute msvsmon como un usuario que tiene permiso para llamar en el equipo local. Esto indica que el usuario debe ser un usuario de dominio y administrador en el equipo de msvsmon. Puede especificar la cuenta de usuario para ejecutar msvsmon de dos maneras:  
  
    -   Haga clic en el icono de msvsmon y elija **ejecución** en el menú contextual  
  
     \- o -  
  
    -   En el símbolo del sistema, ejecute `runas.exe`.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)