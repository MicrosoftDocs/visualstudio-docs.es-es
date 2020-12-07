---
title: -NoSplash (devenv.exe)
description: Obtenga información sobre cómo usar el modificador NoSplash de la línea de comandos de devenv para impedir que se muestre la pantalla de presentación.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86398663ea7b6c8209d4123ab3cb12651d4491e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96044003"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Impide que se muestre la pantalla de presentación.

## <a name="syntax"></a>Sintaxis

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumentos

- *File1*

  Opcional. Archivo que se abrirá en una instancia existente de Visual Studio. Si no existe ninguna instancia de Visual Studio, se creará una instancia con un diseño de ventana simplificado y la herramienta abrirá *File1* en la nueva instancia.

- *FileN*

  Opcional. Uno o más archivos adicionales que se abrirán en la instancia existente de Visual Studio.

## <a name="remarks"></a>Comentarios

Este modificador oculta la pantalla de presentación. Al omitir el modificador, se mostrará la pantalla de presentación. Para examinar con más detalle la pantalla de presentación (por ejemplo, para comprobar el icono del producto de VSPackage), use el modificador [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

El modificador `/NoSplash` puede combinarse con otros modificadores, como [/Run](run-devenv-exe.md) o [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Ejemplo

En los tres ejemplos, se abre el IDE sin mostrar la pantalla de presentación. En el segundo ejemplo también se compila la solución especificada y se ejecuta el archivo ejecutable compilado. En el tercero, se abre el ejecutable especificado para su depuración en el IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Modificadores de línea de comandos Devenv para el desarrollo de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
