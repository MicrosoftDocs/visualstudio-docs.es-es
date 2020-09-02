---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4dde30ebcda46d75271b15ec5b7f7c1ac49f384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150118"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el valor de un registro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 de Un valor de la enumeración de [enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) que especifica en qué registro se va a obtener el valor.  
  
 `pRetVal`  
 enuncia Devuelve el valor actual del registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 A pesar del tamaño del `pRetVal` parámetro, una implementación debe almacenar solo lo que normalmente contiene el registro. Por ejemplo, un registro de 8 bits solo contiene los 8 bits más bajos del valor especificado. Este valor de 8 bits se expande a 64 bits cuando se devuelve desde este método.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
