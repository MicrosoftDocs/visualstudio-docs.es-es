---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 601f20c530ec5e275139d1e70d3df58fa88cd715
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147636"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permite la creación de objetos en el proceso del depurador al código que es fuera de proceso al depurador.  
  
> [!IMPORTANT]
>  No se debe implementar este método, porque permite código no seguro crear objetos arbitrarios en un subproceso del depurador de confianza.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
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
  
 El método no está implementado actualmente.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebugger (Interfaz)](../../winscript/reference/iapplicationdebugger-interface.md)