---
title: Abrir proyecto (comando)
description: Obtenga información sobre el comando Abrir proyecto y cómo abre un proyecto o una solución existentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881976"
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
