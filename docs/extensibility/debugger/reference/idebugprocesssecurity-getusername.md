---
title: IDebugProcessSecurity::GetUserName | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fd3f7133652cf048bb1b4c7a2e7d4886b1c79a2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931095"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtiene el nombre de usuario desde el proveedor del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrUserName`  
 [out] Una cadena que contiene el nombre de usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`. En caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 `GetUserName` Devuelve el nombre de usuario que se muestra en el **nombre de usuario** columna de la **asociar al proceso** cuadro de diálogo. Para ver el **asociar al proceso** cuadro de diálogo, haga clic en **asociar al proceso** en el **herramientas** menú en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)