---
title: Abrir archivo (Comando)
description: Obtenga información sobre el comando Abrir archivo y cómo abre un archivo existente y le permite especificar un editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792fe50aea43bc9711a58a895be09f85c041345b
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304111"
---
# <a name="open-file-command"></a>Abrir archivo (Comando)

Abre un archivo existente y le permite especificar un editor.

## <a name="syntax"></a>Sintaxis

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumentos

`filename`

Obligatorio. Ruta de acceso completa o parcial y nombre del archivo que se va a abrir. Las rutas de acceso que contienen espacios deben ir entre comillas.

## <a name="switches"></a>Conmutadores

/e:`editorname`

Opcional. Nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.

La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el cuadro de diálogo Abrir con, incluidos entre comillas.

Por ejemplo, para abrir un archivo en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Comentarios

A medida que va escribiendo una ruta de acceso, la finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos.

## <a name="example"></a>Ejemplo

En este ejemplo se abre el archivo de estilo "Test1.css" en el editor de código fuente.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Inmediato (ventana)](../../ide/reference/immediate-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
