---
title: Abrir proyecto (comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
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
ms.openlocfilehash: 0ff848ded38b0f59d3894ec4f78dd79ec9d182b8
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924153"
---
# <a name="open-project-command"></a>Comando Abrir proyecto

Abre un proyecto o una solución existentes

## <a name="syntax"></a>Sintaxis

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumentos

`filename`

Obligatorio. La ruta de acceso completa y el nombre de archivo del proyecto o de la solución que se va a abrir.

> [!NOTE]
> La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios se incluyan entre comillas.

## <a name="remarks"></a>Comentarios

La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.

Este comando no está disponible durante la depuración.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se abre el proyecto de Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)