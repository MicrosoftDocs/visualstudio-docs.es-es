---
description: Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP.
title: Uso de dirección IP por parte del sitio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
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
ms.openlocfilehash: fa18ea975bacbda38a18c27d19d438ab5b4da0b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146747"
---
# <a name="error-site-uses-ip-address"></a>Error: Uso de dirección IP por parte del sitio
Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP. Esto ocurre si se cambia **Identificación del sitio Web** a **Usar una dirección IP específica** en IIS.

 Para que funcione la asociación automática, es preciso crear el proyecto con la dirección IP específica en lugar de hacerlo simplemente con el nombre del equipo. De lo contrario, el depurador cambiará el nombre de equipo a localhost, lo que generará un error al enviar el verbo de depuración a IIS.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Utilice la asociación manual (en el menú Depurar, elija **Asociar al proceso**).

     -O bien-

2. Cambie el valor de configuración de **Identificación del sitio Web de IIS**.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
