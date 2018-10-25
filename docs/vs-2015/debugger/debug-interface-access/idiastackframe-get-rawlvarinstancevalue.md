---
title: Get_rawlvarinstancevalue | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ee04a345d95ee521c13f2023ab4a5a525003dac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887181"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este método recupera el valor de la variable local indicada como bytes sin formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pInstance`  
 [in] Un `IDiaLVarInstance` que representa una instancia de la variable local para obtener el valor para el objeto.  
  
 `cbDataMax`  
 [in] Número máximo de bytes en el búfer señalado por `pbData`. Esto puede tener un máximo de 8 bytes (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Devuelve el número real de bytes almacenados en el búfer.  
  
 `pbData`  
 [out] Un búfer que se va a rellenar con datos. No puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



