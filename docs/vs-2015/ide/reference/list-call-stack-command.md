---
title: Mostrar pila de llamadas (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657659"
---
# <a name="list-call-stack-command"></a>Mostrar pila de llamadas (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra la pila de llamadas actual.

## <a name="syntax"></a>Sintaxis

```
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumentos
 `index` Opcional. Establece el marco de pila actual y no muestra ninguna salida.

## <a name="switches"></a>Modificadores
 Cada modificador se puede invocar mediante su forma completa o una forma abreviada.

 /Count: `number` [o]/c: `number` opcional. Número máximo de pilas de llamadas para mostrar. El valor predeterminado es Unlimited.

 /ShowTypes: `yes`&#124;`no` [o]/t: `yes`&#124;`no` opcional. Especifica si se mostrarán o no los tipos de parámetros. El valor predeterminado es `yes`.

 /ShowNames: `yes`&#124;`no` [o]/n: `yes`&#124;`no` opcional. Especifica si se mostrarán o no los nombres de parámetros. El valor predeterminado es `yes`.

 /ShowValues: `yes`&#124;`no` [o]/v: `yes`&#124;`no` opcional. Especifica si se mostrarán o no los valores de parámetros. El valor predeterminado es `yes`.

 /ShowModule: `yes`&#124;`no` [o]/m: `yes`&#124;`no` opcional. Especifica si se mostrará o no el nombre de módulo. El valor predeterminado es `yes`.

 /ShowLineOffset: `yes`&#124;`no` [o]/#: `yes`&#124;`no` opcional. Especifica si se mostrará o no el desplazamiento de línea. El valor predeterminado es `no`.

 /ShowByteOffset: `yes`&#124;`no` [o]/b: `yes`&#124;`no` opcional. Especifica si se mostrará o no el desplazamiento de bytes. El valor predeterminado es `no`.

 /ShowLanguage: `yes`&#124;`no` [o]/l: `yes`&#124;`no` opcional. Especifica si se mostrará o no el idioma. El valor predeterminado es `no`.

 /IncludeCallsAcrossThreads: `yes`&#124;`no` [o]/i: `yes`&#124;`no` opcional. Especifica si se deben incluir llamadas a otros subprocesos o desde otros subprocesos. El valor predeterminado es `no`.

 /ShowExternalCode: `yes`&#124;`no` opcional. Especifica si se debe mostrar Solo mi código para la pila de llamadas. Cuando Solo mi código está desactivado, se muestra todo el código que no es del usuario. Cuando Solo mi código está activado, el código de usuario se muestra como `[external]` en la salida de la pila de llamadas.

 Subproceso: `n` opcional. Muestra la pila de llamadas del subproceso `n`. Si no se especifica ningún subproceso, muestra la pila de llamadas del subproceso actual.

## <a name="remarks"></a>Observaciones
 Los cambios realizados en los argumentos o los modificadores se aplican a las invocaciones posteriores de este comando. Si emite el propio Debug.ListCallStackby, se muestra la pila de llamadas completa. Si, por ejemplo, especifica un índice,

```
Debug.ListCallStack 2
```

 el marco de pila actual se establece en ese marco (en este caso, el segundo marco).

 También puede escribir este comando usando su alias predefinido, kb. Por ejemplo, puede escribir

```
kb 2
```

 para establecer el marco de pila en el segundo marco.

## <a name="example"></a>Ejemplo

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Consulte también
 Lista de [comandos de desensamblado](../../ide/reference/list-disassembly-command.md) comando de [subprocesos comandos](../../ide/reference/list-threads-command.md) de [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) de la [ventana de comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
