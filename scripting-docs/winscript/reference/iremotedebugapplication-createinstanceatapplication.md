---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Permite la creación de objetos en el proceso de aplicación por código que es fuera de proceso a la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Identificador de clase (CLSID) del objeto que se va a crear.  
  
 `pUnkOuter`  
 [in] Si `NULL`, no se crea el objeto como parte de un agregado. En caso contrario, `pUnkOuter` es un puntero para el objeto agregado `IUnknown` interfaz (el control `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexto para el código ejecutable. Los valores se toman de la enumeración `CLSCTX`.  
  
 `riid`  
 [in] El identificador de interfaz que se utiliza para comunicarse con el objeto.  
  
 `ppvObject`  
 [out] Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en `riid`. Tras la devolución es correcta, *`ppvObject` contiene el puntero de interfaz solicitada. En caso de error, \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método delega en `CoCreateInstance`.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (Interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)