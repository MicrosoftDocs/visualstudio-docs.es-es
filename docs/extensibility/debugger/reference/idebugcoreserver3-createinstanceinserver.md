---
title: IDebugCoreServer3::CreateInstanceInServer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords: IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a89657949938526fa8e53689ea04015253b52520
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea una instancia de un motor de depuración en el servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szDll`  
 [in] Ruta de acceso a la dll que implementa el CLSID especificado en el `clsidObject` parámetro. Si se trata de `NULL`, a continuación, COM `CoCreateInstance` función se invoca.  
  
 `wLangId`  
 [in] Configuración regional del motor de depuración. Esto puede ser 0 si la [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) método no debe llamarse.  
  
 `clsidObject`  
 [in] Identificador CLSID del motor de depuración para crear.  
  
 `riid`  
 [in] Id. de interfaz de la interfaz específica para recuperar desde el objeto de clase.  
  
 `ppvObject`  
 [out] `IUnknown` interfaz desde el objeto con instancias. Convertir o calcular las referencias de este objeto a la interfaz deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)