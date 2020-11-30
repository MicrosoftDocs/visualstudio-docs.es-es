---
title: Agregar nuevo elemento (Comando)
description: Aprenda a usar el comando Agregar nuevo elemento para agregar un nuevo elemento de solución o un nuevo conjunto de marcos a la solución actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac07b374ef08a963426b9bfd44f101a8863f04c8
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871293"
---
# <a name="add-new-item-command"></a>Agregar nuevo elemento (Comando)
Agrega un nuevo elemento de solución (como un archivo .htm, .css o .txt o un conjunto de marcos) a la solución actual y lo abre.

## <a name="syntax"></a>Sintaxis

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumentos
`filename`\
Opcional. La ruta de acceso y el nombre de archivo del elemento que se va a agregar a la solución.

## <a name="switches"></a>Conmutadores
/t: `templatename`\
Opcional. Especifica el tipo de archivo que se va a crear. Si no se proporciona ningún nombre de plantilla, se crea un archivo de texto de manera predeterminada.

La sintaxis del argumento /t:`templatename` refleja la información que se encuentra en el cuadro de diálogo **Agregar nuevo elemento de solución**. Tiene que especificar la categoría completa seguida del tipo de archivo; para ello, separe el nombre de categoría del tipo de archivo con una barra inversa (`\`) e incluya la cadena completa entre comillas.

Por ejemplo, para crear un archivo de texto nuevo tiene que escribir lo siguiente para el argumento /t:`templatename`.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
Opcional. El nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.

La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el **cuadro de diálogo Abrir con**, incluidos entre comillas.

Por ejemplo, para abrir una hoja de estilos en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Ejemplo
En este ejemplo se agrega un elemento de solución nuevo, MyHTMLpg, a la solución actual.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
