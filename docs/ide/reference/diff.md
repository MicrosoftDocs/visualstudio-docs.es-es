---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf58c25611fd52c6e8db8e8210101e1c80153275
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844543"
---
# <a name="diff"></a>/Diferencias
Compara dos archivos. Las diferencias se muestran en una ventana especial de Visual Studio.

## <a name="syntax"></a>Sintaxis

```cmd
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