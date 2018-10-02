---
title: IDebugProgramNode2::GetEngineInfo | Documentos de Microsoft
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
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42faae15c9e34bad603cfb0093830909282d544c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580532"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProgramNode2::GetEngineInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnode2-getengineinfo).  
  
Obtiene el nombre y el identificador del motor de depuración (DE) ejecuta un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrEngine`  
 [out] Devuelve el nombre de la DE ejecutar el programa (específicas de C++: Esto puede ser un puntero null que indica que el llamador no está interesado en el nombre del motor).  
  
 `pguidEngine`  
 [out] Devuelve el identificador único global de la DE ejecutar el programa (específicas de C++: Esto puede ser un puntero null que indica que el llamador no está interesado en el GUID del motor).  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

