---
title: Compatibilidad de .NET Core
description: Este documento describe la compatibilidad de versiones de .NET Core en Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 08/20/2019
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: ad23044792d2c21c075e70107b74984d54de2bd3
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714530"
---
# <a name="net-core-support"></a>Compatibilidad de .NET Core

En la tabla siguiente se describen las versiones de .NET Core que admiten las versiones preliminares y estables de Visual Studio para Mac:

| Versión del SDK de .NET Core |Visual Studio para Mac 8.1 (estable) | Visual Studio para Mac 8.2 (estable) | Visual Studio para Mac 8.3 (estable) |
|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|

> [!IMPORTANT]
> No se admiten las versiones preliminares del SDK de .NET Core. Actualice a la versión más reciente. Al instalar Visual Studio para Mac 8.3, se instalará la versión más reciente de .NET Core v3.0.

> [!IMPORTANT]
> Si antes usaba .NET Core v2.2.1xx con Visual Studio para Mac 8.0, deberá actualizar manualmente a una versión compatible de .NET Core, tal y como se muestra en la tabla anterior. Se recomiendan las versiones [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) o [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2).

* .NET Core v3.0 está instalado de manera predeterminada para 8.3.
* .NET Core v2.1.701 (v2.1.700 para 8.1) se instala de manera predeterminada con el instalador.
* Para descargar cualquier otra versión de .NET Core, visite la [página de dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Al usar .NET Core 3.0, se usará C# versión 8 de forma predeterminada. C# 7.3 es el valor predeterminado cuando se usa .NET Core 2.x. Para obtener más información, consulte [Control de versiones del lenguaje C#](/dotnet/csharp/language-reference/configure-language-version).
* Para obtener información acerca de cómo instalar una versión preliminar de Visual Studio para Mac, consulte la guía de [instalación de una versión preliminar](/visualstudio/mac/install-preview).
