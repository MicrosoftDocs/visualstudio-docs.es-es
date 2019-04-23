---
title: 'Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar el equipo en la red. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8eebd082df031161604bd04afe61d1aca652f6a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043289"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar el equipo en la red.
Este comportamiento se produce si se da una de las condiciones siguientes:

- La conexión al equipo remoto se interrumpe.

- La cuenta de usuario en el equipo remoto está deshabilitada.

- La contraseña en el equipo remoto ha expirado.

### <a name="to-resolve-this-behavior"></a>Para solucionar este comportamiento

- Asegúrese de que el equipo local y el equipo remoto están en la misma red. Para ello, utilice el Explorador de Microsoft Windows (o el Explorador de archivos) para intentar tener acceso al equipo remoto.

     — y —

- Asegúrese de que la cuenta de usuario que utiliza para conectarse al equipo remoto esté habilitada.

     — y —

- Asegúrese de que la contraseña que utiliza para conectarse al equipo remoto sea válida y no haya expirado.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)