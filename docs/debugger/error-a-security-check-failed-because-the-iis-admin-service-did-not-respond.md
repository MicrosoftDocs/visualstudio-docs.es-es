---
description: Este error se produce cuando el servicio de administración de IIS no responde.
title: Error de una comprobación de seguridad debido a la falta de respuesta del servicio de administración de IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42c0a5a1a1fdb3a997f46a6933df9c8681fe0498
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147087"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Error: Error de una comprobación de seguridad debido a la falta de respuesta del servicio de administración de IIS
Este error se produce cuando el servicio de administración de IIS no responde. En general, esto indica que hay un problema relacionado con la instalación de IIS. Lo primero que debe hacer es comprobar que el servicio se está ejecutando mediante la herramienta **Servicios** de **Herramientas administrativas**.

### <a name="to-correct-this-error"></a>Para corregir este error

- Reinstale IIS mediante el subprograma **Agregar o quitar programas** del Panel de control.

- o bien

- Quite IIS del equipo mediante el subprograma Agregar o quitar programas del Panel de control. Si el problema persiste tras quitar IIS, compruebe el Registro y asegúrese de que la siguiente clave ya no existe:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     o bien

- Deshabilite el servicio de administración de IIS mediante el subprograma Herramientas administrativas del Panel de control. Esto deshabilitará IIS en el equipo.

     Tras la conclusión de cualquiera de estos tres pasos, reinicie el equipo.

     Para obtener más información, consulte la documentación de IIS.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
