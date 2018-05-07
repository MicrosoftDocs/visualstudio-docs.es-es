---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diferencias
Compara dos archivos. Las diferencias se muestran en una ventana especial de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Argumentos
 `SourceFile`

 Obligatorio. Ruta de acceso completa y nombre del primer archivo que se va a comparar.

 `TargetFile`

 Obligatorio. Ruta de acceso completa y nombre del segundo archivo que se va a comparar.

 `SourceDisplayName`

 Opcional. Nombre para mostrar del primer archivo.

 `TargetDisplayName`

 Opcional. Nombre para mostrar del segundo archivo.