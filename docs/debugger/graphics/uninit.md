---
title: UnInit | Microsoft Docs
description: Use el método UnInit() de VsgDbg para finalizar y cerrar el archivo de registro de gráficos y liberar recursos de registro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905019"
---
# <a name="uninit"></a>UnInit
Finaliza el archivo de registro de gráficos, lo cierra y libera los recursos utilizados mientras la aplicación estaba grabando activamente información de gráficos.

## <a name="syntax"></a>Sintaxis

```C++
void UnInit();
```

## <a name="remarks"></a>Comentarios
 Se llama automáticamente a `UnInit` cuando se destruye una instancia de la clase `VsgDbg`. Si la instancia de `VsgDbg` no estaba grabando activamente información de gráficos, no tiene ningún efecto.

 Después de que se haya llamado a `UnInit` en una instancia de la clase `VsgDbg`, se puede crear un nuevo archivo de registro de gráficos llamando a `Init` y finalizarlo llamando a `UnInit`. Se puede repetir tantas veces como se desee utilizar la misma instancia de `VsgDbg` para crear varios archivos de registro de gráficos independientes.

## <a name="see-also"></a>Vea también
- [Init](init.md)