---
title: UnInit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b5a2accd628cd76c259e1397d99bef255b1b23f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721153"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Finaliza el archivo de registro de gráficos, lo cierra y libera los recursos utilizados mientras la aplicación estaba grabando activamente información de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentarios  
 Se llama automáticamente a `UnInit` cuando se destruye una instancia de la clase `VsgDbg`. Si la instancia de `VsgDbg` no estaba grabando activamente información de gráficos, no tiene ningún efecto.  
  
 Después de que se haya llamado a `UnInit` en una instancia de la clase `VsgDbg`, se puede crear un nuevo archivo de registro de gráficos llamando a `Init` y finalizarlo llamando a `UnInit`. Se puede repetir tantas veces como se desee utilizar la misma instancia de `VsgDbg` para crear varios archivos de registro de gráficos independientes.  
  
## <a name="see-also"></a>Vea también  
 [Init](../debugger/init.md)



