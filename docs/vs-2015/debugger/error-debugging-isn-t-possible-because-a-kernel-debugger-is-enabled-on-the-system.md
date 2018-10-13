---
title: 'Error: La depuración&#39;t posible porque un depurador del Kernel está habilitado en el sistema | Microsoft Docs'
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
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acae508dee0e5ed0897af4914a935cc62fabff66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231808"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Error: La depuración&#39;t posible porque un depurador del Kernel está habilitado en el sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al depurar código administrado, podría aparecer el siguiente mensaje de error:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Este mensaje aparece cuando se intenta depurar código administrado:  
  
-   en un sistema con [!INCLUDE[win7](../includes/win7-md.md)] o [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] que se ha iniciado en modo de depuración.  
  
-   la aplicación usa la versión de CLR 2.0, 3.0 o 3.5.  
  
## <a name="solution"></a>Soluciones  
  
#### <a name="to-fix-this-problem"></a>Para corregir este problema  
  
-   Actualice la aplicación para utilizar la versión 4.0 o 4.5 de CLR  
  
     -O bien-  
  
-   Deshabilite la depuración del kernel y depure en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     -O bien-  
  
-   Depure utilizando el depurador de kernel en lugar de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
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



