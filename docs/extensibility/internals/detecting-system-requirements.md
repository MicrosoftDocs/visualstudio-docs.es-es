---
title: Detectando requisitos del sistema | Microsoft Docs
description: Aprenda a configurar el Microsoft Windows Installer para detectar requisitos del sistema, como la edición de Visual Studio que está instalada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4befcf3950c41beba2440e6f023983269137b1f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329814"
---
# <a name="detect-system-requirements"></a>Detectar requisitos del sistema
Un VSPackage no puede funcionar a menos que esté instalado Visual Studio. Al usar Microsoft Windows Installer para administrar la instalación del VSPackage, puede configurar el instalador para que detecte si Visual Studio está instalado. También puede configurarlo para comprobar si hay otros requisitos en el sistema, por ejemplo, una versión concreta de Windows o una cantidad determinada de RAM.

## <a name="detect-visual-studio-editions"></a>Detectar las ediciones de Visual Studio
 Para determinar si está instalada una edición de Visual Studio, compruebe que el valor de la clave del registro **install** es *(REG_DWORD) 1* en la carpeta correspondiente, tal como se muestra en la tabla siguiente. Tenga en cuenta que hay una jerarquía de las ediciones de Visual Studio:

1. Empresa

2. Profesional

3. Comunidad

Cuando se instala una edición más reciente, se agregan las claves del registro para esa edición, así como para las ediciones anteriores. Es decir, si está instalada la edición Enterprise, la clave de **instalación** se establece en *1* para Enterprise, así como en las ediciones Professional y Community. Por lo tanto, solo tiene que comprobar la versión más reciente que necesite.

> [!NOTE]
> En la versión de 64 bits del editor del registro, las claves de 32 bits se muestran **en \\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node**. Las claves de Visual Studio están **en \\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing**.

|Producto|Clave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Shell de Visual Studio 2015 (integrado y aislado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Detectar cuándo se está ejecutando Visual Studio
 El VSPackage no se puede registrar correctamente si Visual Studio se está ejecutando cuando se instala el VSPackage. El instalador debe detectar cuándo se está ejecutando Visual Studio y después rechazar la instalación del programa. Windows Installer no permite usar entradas de tabla para habilitar dicha detección. En su lugar, debe crear una acción personalizada, como se indica a continuación: Use la `EnumProcesses` función para detectar el *devenv.exe* proceso y, a continuación, establezca una propiedad de instalador que se use en una condición de inicio o que muestre condicionalmente un cuadro de diálogo que pida al usuario que cierre Visual Studio.

## <a name="see-also"></a>Consulte también
- [Instale VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
