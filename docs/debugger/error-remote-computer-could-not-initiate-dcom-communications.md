---
description: Se ha producido un error de DCOM cuando el equipo remoto ha intentado comunicarse con el equipo local.
title: El equipo remoto no ha podido iniciar comunicaciones DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86d6c46f338d789d6b113551ac9d99c681290526
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146787"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Error: El equipo remoto no ha podido iniciar comunicaciones DCOM
Se ha producido un error de DCOM cuando el equipo remoto ha intentado comunicarse con el equipo local. El equipo local es el equipo que está

 ejecutando Visual Studio. Este error puede producirse por varias razones:

- El equipo local tiene habilitado un firewall.

- No funciona la autenticación de Windows desde el equipo remoto al equipo local.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Si el equipo local tiene el Firewall de Windows habilitado, consulte [Depuración remota](../debugger/remote-debugging.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.

2. Para comprobar la autenticación de Windows, abra un recurso compartido de archivos en el equipo local desde el servidor remoto.

3. Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.

## <a name="see-also"></a>Vea también
 [Remote Debugging](../debugger/remote-debugging.md)
