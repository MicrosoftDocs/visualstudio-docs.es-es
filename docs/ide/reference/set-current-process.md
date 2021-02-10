---
title: Establecer el proceso actual
description: Obtenga información sobre el comando Establecer proceso actual y cómo establece el proceso especificado como el proceso activo en el depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef9475e9336acd5c10cee604d453706ea7321c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957808"
---
# <a name="set-current-process"></a>Establecer el proceso actual
Establece el proceso especificado como el proceso activo en el depurador.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
`index`

Obligatorio. Índice del proceso.

## <a name="remarks"></a>Comentarios
Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.

## <a name="example"></a>Ejemplo

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
