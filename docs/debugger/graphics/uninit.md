---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1cb7898042ef7f6974d2ac43ca8630232edddfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884933"
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
 [Init](init.md)