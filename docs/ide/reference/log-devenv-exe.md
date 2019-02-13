---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b2e11cb36176aec94528019cdd19bb5fa86c92b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907222"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De forma predeterminada, el archivo de registro se encuentra aquí:

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Versión\>**\\ActivityLog.xml**

en que \<Versión\> es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumentos

- *NameOfLogFile*

  Obligatorio. Nombre y ruta de acceso completa del archivo de registro donde se guardará.

## <a name="remarks"></a>Comentarios

Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.

El registro solo se escribe para las instancias de Visual Studio que ha abierto con el modificador `/Log`.

## <a name="example"></a>Ejemplo

Este ejemplo dirige el registro al archivo `MyVSLog.xml` del directorio principal del usuario.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)