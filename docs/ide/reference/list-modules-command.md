---
title: Mostrar módulos (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595506"
---
# <a name="list-modules-command"></a>Mostrar módulos (Comando)
Enumera los módulos del proceso actual.

## <a name="syntax"></a>Sintaxis

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parámetros
/Address:`yes|no`

Opcional. Especifica si se muestran las direcciones de memoria de los módulos. El valor predeterminado es `yes`.

/Name:`yes|no`

Opcional. Especifica si se muestran los nombres de los módulos. El valor predeterminado es `yes`.

/Order:`yes|no`

Opcional. Especifica si se muestra el orden de los módulos. El valor predeterminado es `no`.

/Path:`yes|no`

Opcional. Especifica si se muestran las rutas de acceso de los módulos. El valor predeterminado es `yes`.

/Process:`yes|no`

Opcional. Especifica si se muestran los procesos de los módulos. El valor predeterminado es `no`.

/SymbolFile:`yes|no`

Opcional. Especifica si se muestran los archivos de símbolos de los módulos. El valor predeterminado es `no`.

/SymbolStatus:`yes|no`

Opcional. Especifica si se muestran los estados de símbolos de los módulos. El valor predeterminado es `yes`.

/Timestamp:`yes|no`

Opcional. Especifica si se muestran las marcas de tiempo de los módulos. El valor predeterminado es `no`.

/Version:`yes|no`

Opcional. Especifica si se muestran las versiones de los módulos. El valor predeterminado es `no`.

## <a name="example"></a>Ejemplo
En este ejemplo se enumeran los nombres de módulo, las direcciones y las marcas de tiempo del proceso actual.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cómo: Uso de la ventana Módulos](../../debugger/how-to-use-the-modules-window.md)
