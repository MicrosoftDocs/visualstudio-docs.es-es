---
title: /ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41e402a9268acecb70c83e26bab0e682d4ec59f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665580"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Restaura la configuración predeterminada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e inicia automáticamente el IDE de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Opcionalmente, restablece la configuración de un archivo .vssettings especificado.

 La configuración predeterminada se determina mediante el perfil que se ha seleccionado cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se ha iniciado por primera vez.

## <a name="syntax"></a>Sintaxis

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumentos
 `SettingsFile` La ruta de acceso completa y el nombre del archivo .vssettings que se va a aplicar a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Para restaurar el perfil de Configuración general de desarrollo, use `General`.

## <a name="remarks"></a>Observaciones
 Si no se especifica ningún elemento `SettingsFile`, se le pedirá que seleccione una colección predeterminada de opciones la próxima vez que inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="example"></a>Ejemplo
 La siguiente línea de comandos se aplica a la configuración almacenada en el archivo `MySettings.vssettings`.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Consulte también
 [Personalizar la configuración de desarrollo en](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) los [modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md) de Visual Studio
