---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8536fe85e58d3c43784d52b85d50015225068141
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581649"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugCoreServer3::CreateInstanceInServer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver).  
  
Crea una instancia de un motor de depuración en el servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Ruta de acceso a la dll que implementa el CLSID especificado en el `clsidObject` parámetro. Si se trata de `NULL`, a continuación, COM `CoCreateInstance` se llama a la función.  
  
 `wLangId`  
 [in] Configuración regional del motor de depuración. Esto puede ser 0 si la [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) no se debe llamar al método.  
  
 `clsidObject`  
 [in] CLSID del motor de depuración para crear.  
  
 `riid`  
 [in] Id. de interfaz de la interfaz específica para recuperar desde el objeto de clase.  
  
 `ppvObject`  
 [out] `IUnknown` interfaz desde el objeto con instancias. Convertir o calcular las referencias de este objeto en la interfaz deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)

