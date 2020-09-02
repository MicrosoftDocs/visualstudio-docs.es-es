---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657922"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que combine los paquetes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.

## <a name="syntax"></a>Sintaxis

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Observaciones
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ejecuta este comando automáticamente cuando instala un paquete de VSIX. Debe ejecutar `devenv.exe /updateconfiguration` después de revisar los archivos de manera que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] actualice la caché de MEF. Esto le permite evaluar si la corrección es adecuada.

## <a name="example"></a>Ejemplo
 La siguiente línea de comandos hace que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] combine los paquetes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en el sistema y compruebe la caché de MEF para detectar cualquier cambio.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Consulte también
 [Personalizar la configuración de desarrollo en](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) los [modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md) de Visual Studio
