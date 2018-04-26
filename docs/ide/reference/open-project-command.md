---
title: Abrir proyecto (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>Abrir proyecto (Comando)
Abre un proyecto existente.

## <a name="syntax"></a>Sintaxis

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumentos
 `filename`

 Obligatorio. Ruta de acceso completa y nombre de archivo del proyecto que se va a abrir.

 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios se incluyan entre comillas.

## <a name="remarks"></a>Comentarios
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.

 Este comando no está disponible durante la depuración.

## <a name="example"></a>Ejemplo
 En este ejemplo, se abre el proyecto Test1 de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)