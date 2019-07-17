---
title: IDiaStackFrame::get_lengthLocals | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthLocals method
ms.assetid: dbc3e544-578a-4f0b-8d20-f21ad4cbb604
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 364783f2287c363b82cf84bdc0e441e82307598e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190551"
---
# <a name="idiastackframegetlengthlocals"></a>IDiaStackFrame::get_lengthLocals
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de bytes de las variables locales que se insertan en la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de bytes de las variables locales.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite la propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
