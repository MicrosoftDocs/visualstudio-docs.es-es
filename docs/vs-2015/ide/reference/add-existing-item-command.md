---
title: Agregar elemento existente (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7686c4db4984188a4f8c4a52343f1386e9edd909
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54797842"
---
# <a name="add-existing-item-command"></a>Agregar elemento existente (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Agrega un archivo existente a la solución actual y lo abre.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Obligatorio. El nombre de archivo y la ruta de acceso completa, con extensión, del elemento que se agregará a la solución actual. Si el nombre de archivo o la ruta de acceso contienen espacios, incluya la ruta de acceso completa entre comillas.  
  
## <a name="switches"></a>Modificadores  
 /e: `editorname`  
 Opcional. Nombre del editor en el que se abrirá el archivo. Si se especifica el argumento pero no se ha proporcionado ningún nombre de editor, aparece el cuadro de diálogo **Abrir con**.  
  
 La sintaxis del argumento /e:`editorname` usa los nombres de editor tal y como aparecen en el **cuadro de diálogo Abrir con**, incluidos entre comillas. Por ejemplo, para abrir una hoja de estilos en el editor de código fuente, tiene que escribir lo siguiente para el argumento /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se agrega el archivo Form1.frm a la solución actual.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
