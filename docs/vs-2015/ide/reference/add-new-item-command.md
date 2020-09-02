---
title: Agregar nuevo elemento (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670208"
---
# <a name="add-new-item-command"></a>Agregar nuevo elemento (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Agrega un nuevo elemento de solución (como un archivo .htm, .css o .txt o un conjunto de marcos) a la solución actual y lo abre.

## <a name="syntax"></a>Sintaxis

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumentos
 `filename` Opcional. La ruta de acceso y el nombre de archivo del elemento que se va a agregar a la solución.

## <a name="switches"></a>Modificadores
 /t: `templatename` Opcional. Especifica el tipo de archivo que se va a crear. Si no se proporciona ningún nombre de plantilla, se crea un archivo de texto de manera predeterminada.

 La sintaxis del argumento /t:`templatename` refleja la información que se encuentra en el cuadro de diálogo **Agregar nuevo elemento de solución**. Tiene que especificar la categoría completa seguida del tipo de archivo; para ello, separe el nombre de categoría del tipo de archivo con una barra inversa (`\`) e incluya la cadena completa entre comillas.

 Por ejemplo, para crear un archivo de texto nuevo tiene que escribir lo siguiente para el argumento /t:`templatename`.

```
/t:"General\Style Sheet"
```

 /e: `editorname` Opcional. El nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.

 La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el **cuadro de diálogo Abrir con**, incluidos entre comillas.

 Por ejemplo, para abrir una hoja de estilos en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Ejemplo
 En este ejemplo se agrega un elemento de solución nuevo, MyHTMLpg, a la solución actual.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
