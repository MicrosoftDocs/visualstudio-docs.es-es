---
title: 'Error: Depurar ejecutando&#39;t posible porque un depurador del Kernel está habilitado en el sistema | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba943057da003a0fafee6d6fb8c6082d228779f9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482118"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Error: Depurar ejecutando&#39;t posible porque un depurador del Kernel está habilitado en el sistema
Al depurar código administrado, podría aparecer el siguiente mensaje de error:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Este mensaje aparece cuando se intenta depurar código administrado:  
  
-   en un sistema con [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que se ha iniciado en modo de depuración.  
  
-   la aplicación usa la versión de CLR 2.0, 3.0 o 3.5.  
  
## <a name="solution"></a>Soluciones  
  
#### <a name="to-fix-this-problem"></a>Para corregir este problema  
  
-   Actualice la aplicación para utilizar la versión 4.0 o 4.5 de CLR  
  
     -O bien-  
  
-   Deshabilite la depuración del kernel y depure en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     -O bien-  
  
-   Depure utilizando el depurador de kernel en lugar de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     -O bien-  
  
-   En el depurador de kernel, deshabilite las excepciones en modo de usuario.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Para deshabilitar la depuración del kernel en la sesión actual  
  
-   En el símbolo del sistema, escriba:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Para deshabilitar la depuración del kernel para todas las sesiones (Windows Vista y Windows 7)  
  
1.  En el símbolo del sistema, escriba:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Reinicie el equipo.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Para deshabilitar la depuración del kernel para todas las sesiones (otros sistemas operativos Windows)  
  
1.  Busque el archivo boot.ini en la unidad del sistema (normalmente C:\\). El archivo boot.ini podría estar oculto y ser de solo lectura. Por tanto, tendrá que utilizar el siguiente comando para verlo:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Abra el archivo boot.ini en el Bloc de notas y quite las siguientes opciones:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Reinicie el equipo.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Para depurar con el depurador del kernel  
  
1.  Si el depurador del kernel está enlazado, aparecerá un mensaje que le preguntará si desea continuar la depuración. Haga clic en el botón para continuar.  
  
2.  Podría aparecer un mensaje `User break exception(Int 3).` En tal caso, escriba el siguiente comando de depurador del kernel para seguir depurando:  
  
     `gn`  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)