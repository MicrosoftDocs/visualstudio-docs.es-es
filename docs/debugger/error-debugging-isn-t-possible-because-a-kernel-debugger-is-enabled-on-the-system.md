---
title: No se puede depurar porque un depurador del kernel está habilitado en el sistema | Microsoft Docs
description: Este mensaje aparece cuando se intenta depurar código administrado en un sistema Windows 7 o Windows Vista que se ha iniciado en modo de depuración, y la aplicación utiliza la versión CLR 2.0, 3.0 o 3.5 de CLR.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ced7fb79a11321678ae2963241807e5ddd4600ab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466464"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Error: No se puede depurar porque un depurador del kernel está habilitado en el sistema
Al depurar código administrado, podría aparecer el siguiente mensaje de error:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Este mensaje aparece cuando se intenta depurar código administrado:

- en un sistema con [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que se ha iniciado en modo de depuración.

- la aplicación usa la versión de CLR 2.0, 3.0 o 3.5.

## <a name="solution"></a>Soluciones

#### <a name="to-fix-this-problem"></a>Para corregir este problema

- Actualice la aplicación para utilizar la versión 4.0 o 4.5 de CLR

   -O bien-

- Deshabilite la depuración del kernel y depure en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   -O bien-

- Depure utilizando el depurador de kernel en lugar de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   -O bien-

- En el depurador de kernel, deshabilite las excepciones en modo de usuario.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Para deshabilitar la depuración del kernel en la sesión actual

- En el símbolo del sistema, escriba:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Para deshabilitar la depuración del kernel para todas las sesiones (Windows Vista y Windows 7)

1. En el símbolo del sistema, escriba:

    ```cmd
    bcdedit /debug off
    ```

2. Reinicie el equipo.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Para deshabilitar la depuración del kernel para todas las sesiones (otros sistemas operativos Windows)

1. Busque el archivo boot.ini en la unidad del sistema (normalmente, C:\\). El archivo boot.ini podría estar oculto y ser de solo lectura. Por tanto, tendrá que utilizar el siguiente comando para verlo:

    ```cmd
    dir /ASH
    ```

2. Abra el archivo boot.ini en el Bloc de notas y quite las siguientes opciones:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Reinicie el equipo.

#### <a name="to-debug-with-the-kernel-debugger"></a>Para depurar con el depurador del kernel

1. Si el depurador del kernel está enlazado, aparecerá un mensaje que le preguntará si desea continuar la depuración. Haga clic en el botón para continuar.

2. Podría aparecer un mensaje `User break exception(Int 3).` En tal caso, escriba el siguiente comando de depurador del kernel para seguir depurando:

     `gn`

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
