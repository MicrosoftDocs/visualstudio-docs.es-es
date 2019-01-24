---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29cbcebc5bdc51be4223b2592bbe6ac3ae76525d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086364"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Permite la creación de objetos en el proceso de aplicación mediante código que es fuera de proceso a la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rclsid`  
 [in] Identificador de clase (CLSID) del objeto para crear.  
  
 `pUnkOuter`  
 [in] Si `NULL`, el objeto no se crea como parte de un agregado. En caso contrario, `pUnkOuter` es un puntero al objeto agregado `IUnknown` interfaz (el control `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexto de ejecución de código ejecutable. Los valores se toman de la enumeración `CLSCTX`.  
  
 `riid`  
 [in] El identificador de interfaz que se usa para comunicarse con el objeto.  
  
 `ppvObject`  
 [out] Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en `riid`. Tras la devolución es correcta, *`ppvObject` contiene el puntero de interfaz solicitada. En caso de error, \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método delega a `CoCreateInstance`.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (Interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)