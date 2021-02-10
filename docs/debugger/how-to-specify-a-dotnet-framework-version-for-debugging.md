---
title: Especificación de una versión de .NET Framework para la depuración | Microsoft Docs
description: Especifique una versión anterior de .NET Framework para la depuración. El depurador de Visual Studio admite la depuración de versiones anteriores de .NET Framework, así como de la versión actual.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 197cd51d31729119d48e255d038ad2e53f17a891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908366"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Especificación de una versión de .NET Framework para la depuración (C#, Visual Basic, F#)

El depurador de Visual Studio puede depurar versiones anteriores de Microsoft .NET Framework así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de .NET Framework para la aplicación que se está depurando. Pero si la aplicación ya se está ejecutando e inicia la depuración mediante **Asociar a**, es posible que el depurador no siempre pueda identificar una versión anterior de .NET Framework. Si esto ocurre, aparecerá un mensaje de error que indica,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

En estos casos poco frecuentes en los que se muestra este error, puede establecer una clave del Registro para indicar al depurador qué versión debe usar.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración

1. Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:

    `V1.1.4322`

    Identifique el número de versión correcto y anótelo.

2. Inicie el **Editor del Registro** (regedit).

3. En el **Editor del Registro**, abra la carpeta HKEY_LOCAL_MACHINE.

4. Vaya a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Si la clave no existe, haga clic con el botón derecho en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **Nueva clave**. Asigne el nombre `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` a la nueva clave.

5. Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.

   1. Si la clave no existe, haga clic con el botón derecho en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**. Después, haga clic con el botón derecho en el nuevo valor de cadena, haga clic en **Cambiar nombre** y escriba `CLRVersionForDebugging`.

6. Haga doble clic en **CLRVersionForDebugging**.

7. En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**. Por ejemplo: V1.1.4322

8. Haga clic en **Aceptar**.

9. Cierre el **Editor del Registro**.

     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está usando una versión de .NET Framework admitida por Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.

## <a name="see-also"></a>Vea también
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)