---
title: IDebugProperty3::DestroyObjectID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0db5ef80a1734aedb819c109aa4c27c40224886e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Destruye el identificador único asociado con esta propiedad, que indica que el autor de llamada ya no se ocupa de identificar esta propiedad de forma exclusiva de todas las demás propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de depuración no necesita admitir identificadores únicos de una propiedad (debido a ya realiza un seguimiento de ellos inequívocamente internamente), a continuación, puede devolver simplemente `E_NOTIMPL` para este método.  
  
 Se crean identificadores únicos con una llamada a la [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) método cuando el llamador desea asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)