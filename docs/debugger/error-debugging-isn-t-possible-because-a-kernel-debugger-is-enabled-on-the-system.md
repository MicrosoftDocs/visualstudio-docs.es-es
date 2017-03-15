---
title: "Error: No se puede depurar porque un depurador de kernel est&#225; habilitado en el sistema | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.kernel_dbg_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador de kernel"
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: No se puede depurar porque un depurador de kernel est&#225; habilitado en el sistema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al depurar código administrado, podría aparecer el siguiente mensaje de error:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Este mensaje aparece cuando se intenta depurar código administrado:  
  
-   en un sistema con [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que se ha iniciado en modo de depuración.  
  
-   la aplicación usa la versión de CLR 2.0, 3.0 o 3.5.  
  
## Soluciones  
  
#### Para corregir este problema  
  
-   Actualice la aplicación para utilizar la versión 4.0 o 4.5 de CLR  
  
     \-O bien\-  
  
-   Deshabilite la depuración del kernel y depure en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     \-O bien\-  
  
-   Depure utilizando el depurador de kernel en lugar de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     \-O bien\-  
  
-   En el depurador de kernel, deshabilite las excepciones en modo de usuario.  
  
#### Para deshabilitar la depuración del kernel en la sesión actual  
  
-   En el símbolo del sistema, escriba:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### Para deshabilitar la depuración del kernel para todas las sesiones \(Windows Vista y Windows 7\)  
  
1.  En el símbolo del sistema, escriba:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Reinicie el equipo.  
  
#### Para deshabilitar la depuración del kernel para todas las sesiones \(otros sistemas operativos Windows\)  
  
1.  Busque el archivo boot.ini en la unidad del sistema \(normalmente, C:\\\).  El archivo boot.ini podría estar oculto y ser de solo lectura.  Por tanto, tendrá que utilizar el siguiente comando para verlo:  
  
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
  
#### Para depurar con el depurador del kernel  
  
1.  Si el depurador del kernel está enlazado, aparecerá un mensaje que le preguntará si desea continuar la depuración.  Haga clic en el botón para continuar.  
  
2.  Podría aparecer un mensaje `User break exception(Int 3).` En tal caso, escriba el siguiente comando de depurador del kernel para seguir depurando:  
  
     `gn`  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)