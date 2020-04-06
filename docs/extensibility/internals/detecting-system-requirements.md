---
title: Detección de los requisitos del sistema ? Microsoft Docs
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
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708732"
---
# <a name="detect-system-requirements"></a>Detectar los requisitos del sistema
Un VSPackage no puede funcionar a menos que Visual Studio está instalado. Cuando se usa Microsoft Windows Installer para administrar la instalación de SU VSPackage, puede configurar el instalador para detectar si Visual Studio está instalado. También puede configurarlo para comprobar si el sistema tiene otros requisitos, por ejemplo, una versión determinada de Windows o una cantidad determinada de RAM.

## <a name="detect-visual-studio-editions"></a>Detectar ediciones de Visual Studio
 Para determinar si está instalada una edición de Visual Studio, compruebe que el valor de la clave del Registro **Instalar** es *(REG_DWORD) 1* en la carpeta adecuada, como se muestra en la tabla siguiente. Tenga en cuenta que hay una jerarquía de ediciones de Visual Studio:

1. Enterprise

2. Profesional

3. Comunidad

Cuando se instala una edición más reciente, se agregan las claves del registro para esa edición, así como para ediciones anteriores. Es decir, si se instala la edición Enterprise, la clave **De instalación** se establece en *1* para Enterprise, así como para las ediciones Professional y Community. Por lo tanto, solo debe comprobar la edición más reciente que necesita.

> [!NOTE]
> En la versión de 64 bits del editor del Registro, las claves de 32 bits se muestran en **HKEY_LOCAL_MACHINE.\\** Las claves de Visual Studio se encuentran bajo **HKEY_LOCAL_MACHINE, SOFTWARE,\\Wow6432Node, Microsoft, DevDiv, vs, Servicio**.

|Producto|Clave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, DevDiv, vs, servicio, 14,0, empresa|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, DevDiv, vs, Servicio, 14,0, profesional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, DevDiv, vs, servicio, 14,0, comunidad|
|Shell de Visual Studio 2015 (integrado y aislado)|HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, DevDiv, vs, servicio, 14,0, isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Detectar cuando Visual Studio se está ejecutando
 El VSPackage no se puede registrar correctamente si Visual Studio se está ejecutando cuando se instala el VSPackage. El instalador debe detectar cuándo se está ejecutando Visual Studio y, a continuación, se niega a instalar el programa. Windows Installer no permite usar entradas de tabla para habilitar dicha detección. En su lugar, debe crear una acción `EnumProcesses` personalizada, como se indica a continuación: use la función para detectar el proceso *devenv.exe* y, a continuación, establezca una propiedad de instalador que se use en una condición de inicio o muestre condicionalmente un cuadro de diálogo que solicite al usuario que cierre Visual Studio.

## <a name="see-also"></a>Vea también
- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
