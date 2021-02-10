---
title: Ruta de acceso de símbolos (Comando)
description: Obtenga información sobre el comando Ruta de acceso de símbolos y cómo establece la lista de directorios para que el depurador busque símbolos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72e69300e9dc621ea346c05923168c33bc7065c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967168"
---
# <a name="symbol-path-command"></a>Ruta de acceso de símbolos (Comando)
Establece la lista de directorios para que el depurador busque símbolos.

## <a name="syntax"></a>Sintaxis

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumentos
`pathname`

Opcional. Lista de rutas de acceso delimitada por puntos y comas para que el depurador busque símbolos.

## <a name="remarks"></a>Comentarios
Si no se especifica ningún `pathname`, el comando muestra las rutas de acceso de símbolos actuales.

## <a name="example-1"></a>Ejemplo 1
En este ejemplo, se agregan dos rutas de acceso a la lista de directorios de símbolos.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Ejemplo 2
En este ejemplo, se muestra una lista delimitada por puntos y comas de rutas de acceso de símbolos actuales.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Consulte también

- [Ventana Comandos](../../ide/reference/command-window.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
