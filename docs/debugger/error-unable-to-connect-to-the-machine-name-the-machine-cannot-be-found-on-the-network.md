---
title: "Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar la máquina en la red. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ed30ca3baeb29f92c4d5f02b64c581ef9a37a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar la máquina en la red.
Este comportamiento se produce si se da una de las condiciones siguientes:  
  
-   La conexión al equipo remoto se interrumpe.  
  
-   La cuenta de usuario en el equipo remoto está deshabilitada.  
  
-   La contraseña en el equipo remoto ha expirado.  
  
### <a name="to-resolve-this-behavior"></a>Para solucionar este comportamiento  
  
-   Asegúrese de que el equipo local y el equipo remoto están en la misma red. Para ello, utilice el Explorador de Microsoft Windows (o el Explorador de archivos) para intentar tener acceso al equipo remoto.  
  
     — y —  
  
-   Asegúrese de que la cuenta de usuario que utiliza para conectarse al equipo remoto esté habilitada.  
  
     — y —  
  
-   Asegúrese de que la contraseña que utiliza para conectarse al equipo remoto sea válida y no haya expirado.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)   
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)