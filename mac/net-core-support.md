---
title: Compatibilidad de .NET Core
description: Este documento describe la compatibilidad de versiones de .NET Core en Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: a04d15fc2fc768c2d6896396df5dc0f134d1720b
ms.sourcegitcommit: 67f3bdeee583a4fb41cacc7f38839a737bfecc6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2021
ms.locfileid: "105735530"
---
# <a name="net-core-support"></a>Compatibilidad de .NET Core

En la tabla siguiente se describen las versiones de .NET Core que admiten las versiones preliminares y estables de Visual Studio para Mac:

| Versión del SDK de .NET Core |Visual Studio para Mac 8.1 | Visual Studio para Mac 8.2 | Visual Studio para Mac 8.3 | Visual Studio para Mac 8.4 | Visual Studio para Mac 8.5 | Visual Studio para Mac 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v5.0 | | | | | |✔︎|

> [!IMPORTANT]
> No se admiten las versiones preliminares del SDK de .NET Core. Actualice a la versión más reciente. Al instalar Visual Studio para Mac 8.4, se instalará la versión más reciente de .NET Core v3.1.

> [!IMPORTANT]
> Si antes usaba .NET Core v2.2.1xx con Visual Studio para Mac 8.0, deberá actualizar manualmente a una versión compatible de .NET Core, tal y como se muestra en la tabla anterior. Se recomiendan las versiones [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) o [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2).

* .NET Core v3.1 está instalado de manera predeterminada para 8.4, 8.5 y 8.6.
* .NET Core v3.0 está instalado de manera predeterminada para 8.3.
* .NET Core v2.1.701 (v2.1.700 para 8.1) se instala de manera predeterminada con el instalador.
* Para descargar cualquier otra versión de .NET Core, visite la [página de dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Al usar .NET Core 3.0, se usará C# versión 8 de forma predeterminada. C# 7.3 es el valor predeterminado cuando se usa .NET Core 2.x. Para obtener más información, consulte [Control de versiones del lenguaje C#](/dotnet/csharp/language-reference/configure-language-version).
* Para obtener información acerca de cómo instalar una versión preliminar de Visual Studio para Mac, consulte la guía de [instalación de una versión preliminar](./install-preview.md).