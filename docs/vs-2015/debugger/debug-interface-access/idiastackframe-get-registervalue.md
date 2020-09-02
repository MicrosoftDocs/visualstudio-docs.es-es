---
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8038acf2aef8c34d07e7f21543a597ad7b96fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572996"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el valor de un registro especificado como almacenado en el marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `registerIndex`  
 de Uno de los valores de enumeración de la [enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) .  
  
 `pRetVal`  
 enuncia Valor almacenado en el registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
