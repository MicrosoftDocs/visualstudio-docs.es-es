---
title: Copiar (captura mediante programación) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719085"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura mediante programación)
Copia el contenido del archivo de registro de gráficos (.vsglog) activo en un nuevo archivo.

## <a name="syntax"></a>Sintaxis

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parámetros
 `szNewVSGLog` Nombre del nuevo archivo de registro de gráficos.

## <a name="remarks"></a>Comentarios
 Para copiar la información de gráficos a un nuevo archivo, debe haber capturado ya cierta información de gráficos; de lo contrario, no ocurre nada.