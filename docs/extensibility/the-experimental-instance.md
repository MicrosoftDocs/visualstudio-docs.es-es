---
title: La Instancia Experimental (Experimental Instance) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699036"
---
# <a name="the-experimental-instance"></a>Instancia experimental
Para proteger el entorno de desarrollo de Visual Studio de aplicaciones no probadas que podrían cambiarlo, VSSDK proporciona un espacio experimental que puede usar para experimentar. Las nuevas aplicaciones se desarrollan mediante Visual Studio como de costumbre, pero se ejecutan mediante esta instancia experimental.

 Cada aplicación que tiene un paquete VSIX inicia la instancia experimental de Visual Studio en modo de depuración.

 Si desea iniciar la instancia experimental de Visual Studio fuera de una solución específica, ejecute el siguiente comando en la ventana de comandos:

 " Ruta de instalación de*\<Visual Studio>* de la ruta de instalación de Visual Studio>de la ruta de instalación de Visual Studio .

> [!NOTE]
> La instancia experimental se escribe `<version number>Exp` en `<version number>Exp_Config` el registro bajo el y nodos. Por ejemplo, el área de registro experimental de Visual Studio 2015 es
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` y `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Le recomendamos que ejecute la extensión en la instancia experimental mientras la está desarrollando. Al implementar la extensión, se ejecuta en la instancia de desarrollo. Para obtener más información sobre el registro de aplicaciones, vea Registro de [VSPackages](../extensibility/internals/registering-vspackages.md).
