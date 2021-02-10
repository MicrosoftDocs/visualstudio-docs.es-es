---
title: Mostrar código fuente (Comando)
description: Obtenga información sobre el comando Mostrar código fuente y cómo muestra las líneas de código fuente especificadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4efd5ab0ddd94b17fa6a683366707d635f844bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919436"
---
# <a name="list-source-command"></a>Mostrar código fuente (Comando)
Muestra las líneas de código fuente especificadas.

## <a name="syntax"></a>Sintaxis

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Conmutadores
/Count:`number`

Opcional. Especifica el número de líneas que se van a mostrar.

/Current

Opcional. Muestra la línea actual.

/File:`filename`

Opcional. Ruta de acceso del archivo que se va a mostrar. Si no se especifica ningún nombre de archivo, el comando muestra el código fuente para la línea de la instrucción actual.

/Line:`number`

Opcional. Muestra un número de línea concreto.

/ShowLineNumbers:`yes|no`

Opcional. Especifica si se mostrarán o no los números de línea.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra el código fuente desde la línea 4 del archivo Form1.vb, con los números de línea visibles.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)