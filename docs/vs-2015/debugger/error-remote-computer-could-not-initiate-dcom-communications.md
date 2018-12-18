---
title: 'Error: El equipo remoto no pudo iniciar comunicaciones DCOM | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c86e5a193348a8f90e4888e0df3472d102beb08
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800879"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Error: El equipo remoto no ha podido iniciar comunicaciones DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se ha producido un error de DCOM cuando el equipo remoto ha intentado comunicarse con el equipo local. El equipo local es el equipo que está  
  
 ejecutando Visual Studio. Este error puede producirse por varias razones:  
  
-   El equipo local tiene habilitado un firewall.  
  
-   No funciona la autenticación de Windows desde el equipo remoto al equipo local.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Si el equipo local tiene habilitado el Firewall de Windows, consulte [establecer las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
2.  Para comprobar la autenticación de Windows, abra un recurso compartido de archivos en el equipo local desde el servidor remoto.  
  
3.  Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## <a name="see-also"></a>Vea también  
 [Configurar las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



