---
title: Especificar una versión de .NET Framework para la depuración | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d612c3f0a542fe30e9241b43c1df5d82a09832fd
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535974"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Especifique una versión anterior de .NET Framework para la depuraciónC#( F#, Visual Basic,)

El depurador de Visual Studio admite la depuración de versiones anteriores del marco de Microsoft .NET, así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de la .NET Framework para la aplicación que está depurando. Sin embargo, si la aplicación ya se está ejecutando y se inicia la depuración con **adjuntar a**, es posible que el depurador no siempre pueda identificar una versión anterior de la .NET Framework. Si esto ocurre, aparecerá un mensaje de error que indica,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

En los casos excepcionales en los que aparece este error, puede establecer una clave del registro para indicar al depurador qué versión usar.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración

1. Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:

    `V1.1.4322`

    Identifique el número de versión correcto y anótelo.

2. Inicie el **Editor del Registro** (regedit).

3. En el **Editor del Registro**, abra la carpeta HKEY_LOCAL_MACHINE.

4. Navegue a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Si la clave no existe, haga clic con el botón derecho en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **Nueva clave**. Asigne a la nueva clave el nombre `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.

   1. Si la clave no existe, haga clic con el botón derecho en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**. A continuación, haga clic con el botón secundario en el nuevo valor de cadena, haga clic en **cambiar nombre**y escriba `CLRVersionForDebugging`.

6. Haga doble clic en **CLRVersionForDebugging**.

7. En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**. Por ejemplo: V1.1.4322

8. Haga clic en **Aceptar**.

9. Cierre el **Editor del Registro**.

     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está usando una versión de la .NET Framework compatible con Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.

## <a name="see-also"></a>Vea también
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)