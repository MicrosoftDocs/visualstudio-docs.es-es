---
title: Comando Registrar resultados de la ventana Comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666863"
---
# <a name="log-command-window-output-command"></a>Registrar resultados de la ventana de comandos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Copia en un archivo todas las entradas y salidas de la ventana **Comandos**.

## <a name="syntax"></a>Sintaxis

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumentos
 `filename` Opcional. Nombre del archivo de registro. De forma predeterminada, el archivo se crea en la carpeta de perfil del usuario. Si ya existe el nombre de archivo, el registro se anexa al final del archivo existente. Si no se especifica ningún archivo, se usa el último archivo especificado. Si no existe ningún archivo anterior, se crea un archivo de registro predeterminado, denominado cmdline.log.

> [!TIP]
> Para cambiar la ubicación en la que se guarda el archivo de registro, escriba la ruta de acceso completa del archivo, entre comillas si la ruta de acceso contiene algún espacio.

## <a name="switches"></a>Modificadores
 /on opcional. Inicia el registro de la ventana **Comandos** en el archivo especificado y anexa el archivo con la nueva información.

 /off opcional. Detiene el registro de la ventana **Comandos**.

 /overwrite opcional. Si el archivo especificado en el argumento `filename` coincide con un archivo existente, se sobrescribe.

## <a name="remarks"></a>Observaciones
 Si no se especifica ningún archivo, se crea el archivo cmdline.log de forma predeterminada. De manera predeterminada, el alias de este comando es Log.

## <a name="examples"></a>Ejemplos
 Este ejemplo crea un archivo de registro, cmdlog, e inicia el registro de comandos.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Este ejemplo detiene el registro de comandos.

```
>Tools.LogCommandWindowOutput /off
```

 Este ejemplo reanuda el registro de comandos en el archivo de registro usado anteriormente.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
