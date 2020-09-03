---
title: 'IDebugProgramNodeAttach2:: alattach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148536"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se adjunta al programa asociado o pospone el proceso de asociación al método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidProgramId`  
 [in] `GUID` para asignar al programa asociado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se debe llamar al método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método durante el proceso de adjuntar, antes de llamar al método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . El `OnAttach` método puede realizar el proceso de asociación en sí mismo (en cuyo caso, este método devuelve `S_FALSE` ) o aplazar el proceso de asociación al `IDebugEngine2::Attach` método (el `OnAttach` método devuelve `S_OK` ). En cualquiera de los dos eventos, el `OnAttach` método puede establecer el `GUID` del programa que se está depurando en el especificado `GUID` .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
