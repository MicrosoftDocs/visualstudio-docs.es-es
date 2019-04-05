---
title: 'Error: No se puede iniciar la comunicación DCOM | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 514f4e3de9bd5b79387a17dffe0e016dc92ea91e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987952"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Error: No se puede iniciar la comunicación con DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se ha producido un error de DCOM cuando el equipo local ha intentado comunicarse con el equipo remoto. Esto se debe a la presencia de un firewall en el servidor remoto o a un incumplimiento de la autenticación de Windows en el equipo remoto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Si el equipo remoto tiene habilitado el Firewall de Windows, consulte [establecer las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
-   Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## <a name="see-also"></a>Vea también  
 [Remote Debugging](../debugger/remote-debugging.md)
