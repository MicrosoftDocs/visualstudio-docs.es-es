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
ms.openlocfilehash: b674239d4d3b800680479830fbb16392e0cdeaf4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713560"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Cómo: especificar una versión de .NET Framework para la depuración (C#, Visual Basic, F#)

El depurador de Visual Studio admite la depuración en versiones anteriores de Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para la aplicación que se está depurando. Sin embargo, si la aplicación ya está funcionando y que inicie la depuración mediante el uso de **adjuntar a**, el depurador no siempre puede identificar una versión anterior de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Si esto ocurre, aparecerá un mensaje de error que indica,

``` cmd
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.
```

En los casos excepcionales, donde aparece este error, puede establecer una clave del registro para indicar al depurador qué versión debe utilizar.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración

1. Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:

    `V1.1.4322`

    Identifique el número de versión correcto y anótelo.

2. Inicie el **Editor del Registro** (regedit).

3. En el **Editor del Registro**, abra la carpeta HKEY_LOCAL_MACHINE.

4. Navegue a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Si la clave no existe, haga clic con el botón derecho en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **Nueva clave**. Nombre de la nueva clave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.

   1.  Si la clave no existe, haga clic con el botón derecho en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**. A continuación, haga clic en el nuevo valor de cadena, haga clic en **cambiar el nombre de**y el tipo `CLRVersionForDebugging`.

6. Haga doble clic en **CLRVersionForDebugging**.

7. En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**. Por ejemplo: V1.1.4322

8. Haga clic en **Aceptar**.

9. Cierre el **Editor del Registro**.

     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está utilizando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] admitida por Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.

## <a name="see-also"></a>Vea también
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)