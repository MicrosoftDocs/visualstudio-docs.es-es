---
title: 'Error: No se puede iniciar la comunicación DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dc250666c5f60064016b90121f7238f9e6e19ae
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682731"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Error: No se puede iniciar la comunicación con DCOM
Se ha producido un error de DCOM cuando el equipo local ha intentado comunicarse con el equipo remoto. Esto se debe a la presencia de un firewall en el servidor remoto o a un incumplimiento de la autenticación de Windows en el equipo remoto.

### <a name="to-correct-this-error"></a>Para corregir este error

-   Si el equipo remoto tiene habilitado el Firewall de Windows, consulte [depuración remota](../debugger/remote-debugging.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.

-   Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)