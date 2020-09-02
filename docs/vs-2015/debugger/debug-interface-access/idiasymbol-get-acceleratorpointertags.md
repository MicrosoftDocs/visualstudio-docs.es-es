---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149841"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devuelve todos los valores de etiqueta de puntero de acelerador que corresponden a una función de código auxiliar de acelerador de C++ AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cnt`  
 de Tamaño de la matriz de salida `pPointerTags` .  
  
 `pcnt`  
 enuncia Recuento de etiquetas de puntero de acelerador en la función de código auxiliar del acelerador C++ AMP.  
  
 `pPointerTags`  
 enuncia `DWORD` Puntero de matriz que se rellena con los valores de la etiqueta de puntero de acelerador en la función de código auxiliar del acelerador C++ amp.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en una `IDiaSymbol` interfaz que corresponde a una función de código auxiliar de acelerador de C++ amp.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
