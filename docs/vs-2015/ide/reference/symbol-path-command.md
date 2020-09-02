---
title: Comando Ruta de acceso de símbolos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651001"
---
# <a name="symbol-path-command"></a>Ruta de acceso de símbolos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece la lista de directorios para que el depurador busque símbolos.

## <a name="syntax"></a>Sintaxis

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumentos
 `pathname` Opcional. Lista de rutas de acceso delimitada por puntos y comas para que el depurador busque símbolos.

## <a name="remarks"></a>Observaciones
 Si no se especifica ningún `pathname`, el comando muestra las rutas de acceso de símbolos actuales.

## <a name="example"></a>Ejemplo
 En este ejemplo, se agregan dos rutas de acceso a la lista de directorios de símbolos.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Ejemplo
 En este ejemplo, se muestra una lista delimitada por puntos y comas de rutas de acceso de símbolos actuales.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Consulte también
 Comandos de la [ventana comandos](../../ide/reference/command-window.md) de [Visual Studio](../../ide/reference/visual-studio-commands.md)
