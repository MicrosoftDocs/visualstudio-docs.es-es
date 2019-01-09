---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 160cbf93cee8ff778a4f84ee833c7fac3d7f26b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830669"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaura la configuración predeterminada de Visual Studio e inicia automáticamente el IDE de Visual Studio. Opcionalmente, restablece la configuración en un archivo *vssettings* especificado.

La configuración predeterminada se determina mediante el perfil que se ha seleccionado cuando se ha iniciado Visual Studio por primera vez.

> [!TIP]
> Para obtener información sobre cómo restablecer la configuración mediante el entorno de desarrollo integrado (IDE), vea [Restablecer la configuración](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sintaxis

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumentos

`SettingsFile`

La ruta de acceso completa y el nombre del archivo *vssettings* que se van a aplicar a Visual Studio.

Para restaurar el perfil de Configuración general de desarrollo, use `General`.

## <a name="remarks"></a>Comentarios

Si no se especifica `SettingsFile`, se le pide que seleccione una colección predeterminada de opciones la siguiente vez que inicie Visual Studio.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos se aplica a la configuración almacenada en el archivo `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Vea también

- [Configuración del entorno](../environment-settings.md)
- [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)