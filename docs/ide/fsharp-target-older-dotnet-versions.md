---
title: Especificar como destino versiones anteriores de .NET Framework para F#
description: Descubra cómo especificar como destino una versión anterior de .NET Framework cuando usa F# en Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572e48328317634f036e8c1301d81c38314a21c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547889"
---
# <a name="target-older-versions-of-net-f"></a>Especificar como destino versiones anteriores de .NET (F#)

El siguiente error puede aparecer si intenta especificar como destino .NET Framework 2.0, 3.0 o 3.5 en un proyecto de F# cuando Visual Studio está instalado en Windows 8.1:

**This project requires the 2.0 F# runtime, but that runtime is not installed.** (Este proyecto requiere el runtime de F# 2.0, pero ese runtime no está instalado).

Tenemos constancia de que este error se produce con la siguiente combinación de condiciones:

- Ha instalado Visual Studio en Windows 8.1.

- No ha habilitado.NET Framework 3.5 antes de instalar Visual Studio.

- El proyecto tiene como destino .NET Framework 2.0, 3.0 o 3.5.

Cuando instala Visual Studio, este detecta las versiones instaladas de .NET Framework. Visual Studio instala el runtime de F# 2.0 solo si .NET Framework 3.5 está instalado y habilitado.

## <a name="resolve-the-error"></a>Resolver el error

Para resolver este error, puede:

- Especificar como destino una versión más reciente de .NET Framework.

- Habilitar .NET Framework 3.5 en Windows 8.1 y, luego, instalar el runtime de F# 2.0 reparando la instalación de Visual Studio. Abajo se indican los pasos necesarios para ello.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Habilitar .NET Framework 3.5 en Windows 8.1

1. En la pantalla **Inicio**, escriba **Panel de control**.

   A medida que escribe, aparecerá el icono de **Panel de control** bajo el encabezado **Aplicaciones**.

2. Haga clic en el icono **Panel de control**, haga clic en el icono **Programas** y, después, elija el vínculo **Activar o desactivar las características de Windows**.

3. Asegúrese de que la casilla **.NET Framework 3.5 (incluye .NET 2.0 y 3.0)** está activada y, luego, haga clic en el botón **Aceptar**. No resulta necesario activar las casillas de todos los nodos secundarios para los componentes opcionales de .NET Framework.

   .NET Framework 3.5 se habilita si no estaba habilitado previamente.

### <a name="to-install-the-f-20-runtime"></a>Para instalar el runtime de F# 2.0

Siga los [pasos para reparar Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Guía de F# (.NET Framework)](/dotnet/fsharp/)
- [F# en Visual Studio](fsharp-visual-studio.md)