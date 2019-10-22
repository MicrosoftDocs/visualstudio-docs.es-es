---
title: Comando Mostrar módulos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659525"
---
# <a name="list-modules-command"></a>Mostrar módulos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera los módulos del proceso actual.

## <a name="syntax"></a>Sintaxis

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parámetros
 /Address: `yes|no` opcional. Especifica si se muestran las direcciones de memoria de los módulos. El valor predeterminado es `yes`.

 /Name:`yes|no` opcional. Especifica si se muestran los nombres de los módulos. El valor predeterminado es `yes`.

 /Order: `yes|no` opcional. Especifica si se muestra el orden de los módulos. El valor predeterminado es `no`.

 /Path:`yes|no` opcional. Especifica si se muestran las rutas de acceso de los módulos. El valor predeterminado es `yes`.

 /Process: `yes|no` opcional. Especifica si se muestran los procesos de los módulos. El valor predeterminado es `no`.

 /SymbolFile: `yes|no` opcional. Especifica si se muestran los archivos de símbolos de los módulos. El valor predeterminado es `no`.

 /SymbolStatus: `yes|no` opcional. Especifica si se muestran los estados de símbolos de los módulos. El valor predeterminado es `yes`.

 /Timestamp: `yes|no` opcional. Especifica si se muestran las marcas de tiempo de los módulos. El valor predeterminado es `no`.

 /Version:`yes|no` opcional. Especifica si se muestran las versiones de los módulos. El valor predeterminado es `no`.

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo
 En este ejemplo se enumeran los nombres de módulo, las direcciones y las marcas de tiempo del proceso actual.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Otras referencias
 [Comandos de Visual Studio ](../../ide/reference/visual-studio-commands.md) [Command ventana ](../../ide/reference/command-window.md) [How: usar la ventana módulos](../../debugger/how-to-use-the-modules-window.md)
