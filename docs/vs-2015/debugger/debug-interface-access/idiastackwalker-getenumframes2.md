---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25090ae66d28ebd9eb62f62f14979de1e82c5302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144715"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un enumerador de marcos de pila para un tipo de plataforma específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cpuid`  
 de Un valor de la enumeración de [enumeración CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , que especifica el tipo de plataforma.  
  
 `pHelper`  
 de Objeto auxiliar [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 enuncia Devuelve un objeto [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) que contiene una lista de objetos [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener una lista de marcos de pila solo para la plataforma x86, llame al método [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Enumeración CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
