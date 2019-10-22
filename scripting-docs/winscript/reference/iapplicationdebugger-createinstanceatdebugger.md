---
title: 'Iapplicationdebugger (:: CreateInstanceAtDebugger | Microsoft Docs'
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
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577890"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permite la creación de objetos en el proceso del depurador mediante el código que está fuera de proceso del depurador.  
  
> [!IMPORTANT]
> Este método no debe implementarse, ya que permite que el código que no es de confianza cree objetos arbitrarios en un subproceso del depurador de confianza.  
  
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
 de Identificador de clase (CLSID) del objeto que se va a crear.  
  
 `pUnkOuter`  
 de Si `NULL`, el objeto no se crea como parte de un agregado. De lo contrario, `pUnkOuter` es un puntero a la interfaz de `IUnknown` del objeto de agregado (control `IUnknown`).  
  
 `dwClsContext`  
 de Contexto para ejecutar el código ejecutable. Los valores se toman de la enumeración `CLSCTX`.  
  
 `riid`  
 de Identificador de interfaz que se usa para comunicarse con el objeto.  
  
 `ppvObject`  
 enuncia Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en `riid`. Si la devolución es correcta, * `ppvObject` contiene el puntero de interfaz solicitado. En caso de error, \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método delega en `CoCreateInstance`.  
  
 El método no está implementado actualmente.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebugger (Interfaz)](../../winscript/reference/iapplicationdebugger-interface.md)