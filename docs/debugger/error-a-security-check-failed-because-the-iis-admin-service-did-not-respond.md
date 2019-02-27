---
title: 'Error: Error en una comprobación de seguridad porque el servicio de administración IIS no respondió | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe294bd375f4896286b32d0d2c638fa8b467061b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688035"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Error: Una comprobación de seguridad produjo un error porque el servicio de administración de IIS no respondió
Este error se produce cuando el servicio de administración de IIS no responde. En general, esto indica que hay un problema relacionado con la instalación de IIS. Lo primero que debe hacer es comprobar que el servicio se está ejecutando mediante la herramienta **Servicios** de **Herramientas administrativas**.

### <a name="to-correct-this-error"></a>Para corregir este error

-   Reinstale IIS mediante el subprograma **Agregar o quitar programas** del Panel de control.

-   o bien

-   Quite IIS del equipo mediante el subprograma Agregar o quitar programas del Panel de control. Si el problema persiste tras quitar IIS, compruebe el Registro y asegúrese de que la siguiente clave ya no existe:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     o bien

-   Deshabilite el servicio de administración de IIS mediante el subprograma Herramientas administrativas del Panel de control. Esto deshabilitará IIS en el equipo.

     Tras la conclusión de cualquiera de estos tres pasos, reinicie el equipo.

     Para obtener más información, consulte la documentación de IIS.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)