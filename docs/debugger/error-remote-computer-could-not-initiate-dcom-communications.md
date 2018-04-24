---
title: 'Error: El equipo remoto no pudo iniciar comunicaciones DCOM | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 111c8b010f9d1415e8e9e4e86e1401346f78702d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Error: El equipo remoto no ha podido iniciar comunicaciones DCOM
Se ha producido un error de DCOM cuando el equipo remoto ha intentado comunicarse con el equipo local. El equipo local es el equipo que está  
  
 ejecutando Visual Studio. Este error puede producirse por varias razones:  
  
-   El equipo local tiene habilitado un firewall.  
  
-   No funciona la autenticación de Windows desde el equipo remoto al equipo local.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Si el equipo local tiene habilitado Firewall de Windows, vea [depuración remota](../debugger/remote-debugging.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
2.  Para comprobar la autenticación de Windows, abra un recurso compartido de archivos en el equipo local desde el servidor remoto.  
  
3.  Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)