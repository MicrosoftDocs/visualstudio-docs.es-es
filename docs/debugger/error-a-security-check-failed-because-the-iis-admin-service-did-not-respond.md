---
title: "Error: Error de una comprobación de seguridad porque el servicio de administración IIS no respondió | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 85b96d9e1396933519da71e93bac075ee51af001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Error: Una comprobación de seguridad produjo un error porque el servicio de administración de IIS no respondió
Este error se produce cuando el servicio de administración de IIS no responde. En general, esto indica que hay un problema relacionado con la instalación de IIS. En primer lugar, compruebe que el servicio se está ejecutando mediante el **servicios** herramienta de **herramientas administrativas**.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Reinstale IIS mediante el **agregar o quitar programas** panel de control.  
  
-   O bien  
  
-   Quite IIS del equipo mediante el subprograma Agregar o quitar programas del Panel de control. Si el problema persiste tras quitar IIS, compruebe el Registro y asegúrese de que la siguiente clave ya no existe:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     O bien  
  
-   Deshabilite el servicio de administración de IIS mediante el subprograma Herramientas administrativas del Panel de control. Esto deshabilitará IIS en el equipo.  
  
     Tras la conclusión de cualquiera de estos tres pasos, reinicie el equipo.  
  
     Para obtener más información, consulte la documentación de IIS.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)