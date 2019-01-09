---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0d2e6af25b4e0acc4aad88c33861e9d22a775b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846131"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De manera predeterminada, el archivo de registro es:

 *% APPDATA %* \Microsoft\VisualStudio\\*Versión*\ActivityLog.xml

 en que *Versión* es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.

## <a name="syntax"></a>Sintaxis

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Comentarios
 Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.

 El registro se escribe para todas las instancias de Visual Studio que se han invocado con el modificador /log. No registra las instancias de Visual Studio que se han invocado sin el modificador.

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)