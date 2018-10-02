---
title: IDebugProgramPublisher2::PublishProgram | Documentos de Microsoft
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
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b38c371cdfd6b6d37ac90f57981b429f2ef2a1dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582944"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProgramPublisher2::PublishProgram](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogrampublisher2-publishprogram).  
  
Este método hace que un programa disponible para los motores de depuración (DEs) y el Administrador de sesión de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Engines`  
 [in] Una matriz de GUID para DEs que puede iniciar o asociar a este programa.  
  
 `szFriendlyName`  
 [in] Nombre descriptivo para el programa (que aparece en los menús o cuadros de diálogo que se presentan al usuario).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interfaz para el programa (este valor se usa como una cookie para identificar de forma única el programa; se utiliza este mismo valor para "anular la publicación" el programa)  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para que un programa ya no está disponible para la depuración, llame a [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)

