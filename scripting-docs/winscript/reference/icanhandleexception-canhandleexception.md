---
title: 'Icanhandleexception (:: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575724"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Determina si el llamador del motor de scripts puede controlar una excepción especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pExcepInfo`  
 de Puntero a una estructura de `EXCEPINFO` que contiene la información que se informará si no se encuentra ningún controlador de excepciones.  
  
 `pvar`  
 de Valor asociado a la excepción, como el valor generado por una instrucción `throw`. Este parámetro puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El autor de la llamada puede controlar la excepción|  
|`E_FAIL`|El autor de la llamada no puede controlar la excepción.|  
  
## <a name="remarks"></a>Comentarios  
 Si una llamada a `IDispatchEx::InvokeEx`, o un método similar, produce una excepción, el motor de scripts comprueba si hay un llamador en la cadena de llamador del script que admita la interfaz de `ICanHandleException` e indica que puede controlar la excepción. Si ningún llamador puede controlar la excepción, se detiene el motor de scripts.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz icanhandleexception (](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)