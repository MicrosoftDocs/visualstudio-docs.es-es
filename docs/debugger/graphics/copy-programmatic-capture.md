---
title: Copiar (Captura mediante programación) | Microsoft Docs
description: Use el método Copiar de la clase VsgDbg para copiar el contenido del archivo de registro de gráficos (.vsglog) activo en un archivo nuevo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727849"
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