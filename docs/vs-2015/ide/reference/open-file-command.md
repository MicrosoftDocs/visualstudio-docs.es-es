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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1a3d363f51861af5914ee0172c5c9a3511b2485
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767358"
---
# <a name="open-file-command"></a>Abrir archivo (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Abre un archivo existente y le permite especificar un editor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Obligatorio. Ruta de acceso completa o parcial y nombre del archivo que se va a abrir. Las rutas de acceso que contienen espacios deben ir entre comillas.  
  
## <a name="switches"></a>Modificadores  
 /e:`editorname`  
 Opcional. Nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el cuadro de diálogo Abrir con, incluidos entre comillas.  
  
 Por ejemplo, para abrir un archivo en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Comentarios  
 A medida que va escribiendo una ruta de acceso, la finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se abre el archivo de estilo "Test1.css" en el editor de código fuente.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Ventana Inmediato](../../ide/reference/immediate-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
