---
title: -Log (devenv.exe)
description: Obtenga información sobre cómo usar el modificador Log de la línea de comandos de devenv para registrar toda la actividad en el archivo de registro para solucionar problemas.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040581"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De forma predeterminada, el archivo de registro se encuentra aquí:

**%APPDATA%\\Microsoft\\VisualStudio\\** \<Version\> **\\ActivityLog.xml**

donde \<Version\> es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumentos

- *NameOfLogFile*

  Obligatorio. Nombre y ruta de acceso completa del archivo de registro donde se guardará.

## <a name="remarks"></a>Observaciones

Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.

El registro solo se escribe para las instancias de Visual Studio que ha abierto con el modificador `/Log`.

## <a name="example"></a>Ejemplo

Este ejemplo dirige el registro al archivo `MyVSLog.xml` del directorio principal del usuario.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
