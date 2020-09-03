---
title: Comando Abrir archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671935"
---
# <a name="open-file-command"></a>Abrir archivo (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre un archivo existente y le permite especificar un editor.

## <a name="syntax"></a>Sintaxis

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumentos
 `filename` Obligatorio. Ruta de acceso completa o parcial y nombre del archivo que se va a abrir. Las rutas de acceso que contienen espacios deben ir entre comillas.

## <a name="switches"></a>Modificadores
 /e:`editorname` opcional. Nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.

 La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el cuadro de diálogo Abrir con, incluidos entre comillas.

 Por ejemplo, para abrir un archivo en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Observaciones
 A medida que va escribiendo una ruta de acceso, la finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos.

## <a name="example"></a>Ejemplo
 En este ejemplo se abre el archivo de estilo "Test1.css" en el editor de código fuente.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [inmediato ventana](../../ide/reference/immediate-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
