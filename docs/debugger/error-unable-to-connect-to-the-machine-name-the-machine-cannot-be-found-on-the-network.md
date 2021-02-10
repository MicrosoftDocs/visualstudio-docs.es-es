---
title: No se puede conectar al equipo &lt;nombre&gt;. No se puede encontrar el equipo en la red. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dcf52a258a46f44afaf6e890531496f57b11fc24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871070"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Error: No se puede conectar al equipo &lt;nombre&gt;. No se puede encontrar el equipo en la red.
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