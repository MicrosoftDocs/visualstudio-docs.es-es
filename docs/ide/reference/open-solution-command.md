---
title: Abrir solución (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 576146e8bcbc20babff10f2a55d561f532a80723
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="open-solution-command"></a>Abrir solución (Comando)
Abre una solución existente y cierra cualquier otra solución abierta.

## <a name="syntax"></a>Sintaxis

```cmd
File.OpenSolution filename
```

## <a name="arguments"></a>Argumentos
 `Filename`

 Obligatorio. La ruta de acceso completa y el nombre de archivo de la solución que se va a abrir.

 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios se incluyan entre comillas.

## <a name="remarks"></a>Comentarios
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.

## <a name="example"></a>Ejemplo
 En este ejemplo se abre la solución Test1.sln.

```cmd
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)