---
title: Mostrar memoria (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c0c2512bd6b446c35aa01e9f56711bb39cd85b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846092"
---
# <a name="list-memory-command"></a>Mostrar memoria (Comando)
Muestra el contenido del intervalo de memoria especificado.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumentos
 `expression`

 Opcional. Dirección de memoria desde la que se va a empezar a mostrar la memoria.

## <a name="switches"></a>Modificadores
 /ANSI&#124;Unicode

 Opcional. Muestra la memoria como caracteres correspondientes a los bytes de memoria, ya sean ANSI o Unicode.

 /Count:`number`

 Opcional. Determina el número de bytes de memoria que se muestran, empezando por `expression`.

 /Format:`formattype`

 Opcional. Tipo de formato para ver la información de memoria en la ventana **Memoria**. Puede ser OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) o Double (64 bits). Si se usa OneByte, `/Unicode` no está disponible.

 /Hex&#124;Signed&#124;Unsigned

 Opcional. Especifica el formato de visualización de números: con signo, sin signo o hexadecimal.

## <a name="remarks"></a>Comentarios
 En lugar de escribir un comando **Debug.ListMemory** completo con todos los modificadores, puede invocar el comando mediante los alias predefinidos con ciertos modificadores preestablecidos en los valores especificados. Por ejemplo, en lugar de especificar:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 puede escribir:

```cmd
>df /Count:30 /Unicode
```

 A continuación se muestra una lista de los alias disponibles para el comando **Debug.ListMemory**:

|Alias|Comandos y modificadores|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Ejemplo

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Vea también

- [Mostrar pila de llamadas (Comando)](../../ide/reference/list-call-stack-command.md)
- [Mostrar subprocesos (Comando)](../../ide/reference/list-threads-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)