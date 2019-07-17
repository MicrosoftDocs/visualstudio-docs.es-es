---
title: IDebugProcessSecurity::GetUserName | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202787"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el nombre de usuario desde el proveedor del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 `GetUserName` Devuelve el nombre de usuario que se muestra en el **nombre de usuario** columna de la **asociar al proceso** cuadro de diálogo. Para ver el **asociar al proceso** cuadro de diálogo, haga clic en **asociar al proceso** en el **herramientas** menú en el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
