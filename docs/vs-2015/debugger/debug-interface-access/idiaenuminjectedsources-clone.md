---
title: IDiaEnumInjectedSources::Clone | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20144ad716d66fc88c7482971218182db9ba30db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995286"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppenum`  
 [out] Devuelve un [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) objeto que contiene un duplicado del enumerador. No se duplican los orígenes insertados, solo el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
