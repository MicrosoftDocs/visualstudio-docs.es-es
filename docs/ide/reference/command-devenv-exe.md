---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf8f72f0d9b0c2d847ddb2c5e7e6c3c8d4ae4467
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932500"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Ejecute el comando especificado después de iniciar el IDE de Visual Studio.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumentos

- *CommandName*

  Obligatorio. Nombre completo de un comando de Visual Studio o su alias, delimitado por comillas dobles. Para obtener más información sobre la sintaxis de comandos y de alias, consulte [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Comentarios

Una vez completado el inicio, el IDE ejecuta el comando indicado. Si usa este modificador, en el IDE no se mostrará la página de inicio de Visual Studio al iniciar la aplicación.

Si un complemento muestra un comando, puede utilizar este modificador para iniciar el complemento desde la línea de comandos. Para obtener más información, vea [Cómo: Control Add-Ins By Using the Add-In Manager](/previous-versions/xwdatdwh(v=vs.140)) (Control de los complementos mediante el Administrador de complementos).

## <a name="example"></a>Ejemplo

En el primer ejemplo se inicia Visual Studio y se ejecuta automáticamente la macro Abrir archivos favoritos.

En el segundo, se abre una pestaña de exploración web en el IDE y se navega al sitio de Microsoft Docs.

En el tercero, se crea un archivo denominado `some_file.cs` y se abre en un editor de código.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Ventana Comandos](command-window.md)