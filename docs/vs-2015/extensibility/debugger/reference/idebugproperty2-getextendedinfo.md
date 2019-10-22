---
title: IDebugProperty2::GetExtendedInfo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164974"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene información de la propiedad extendida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidExtendedInfo`  
 [in] GUID que determina el tipo de información extendida que se va a recuperar. Para obtener más información, vea la sección Comentarios.  
  
 `pExtendedInfo`  
 [out] Devuelve un `VARIANT` (C++) o un objeto (C#) que se puede utilizar para recuperar la información de la propiedad extendida. Por ejemplo, podría devolver este parámetro una `IUnknown` interfaz que puede consultarse para una [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaz. Para obtener más información, vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. Devuelve `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` si no hay ninguna información adicional para recuperar.  
  
## <a name="remarks"></a>Comentarios  
 Este método existe con el fin de recuperar la información que no se presta a la que se recuperan mediante una llamada a la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
 Normalmente se reconocen los GUID siguientes por este método (los valores de GUID se especifican para C#, ya que el nombre no está disponible en cualquier ensamblado). GUID adicionales se pueden crear para uso interno.  
  
|NOMBRE|GUID|DESCRIPCIÓN|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Devuelve un `IUnknown` interfaz al documento. Normalmente, el [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaz puede obtenerse a partir de este `IUnknown` interfaz.|  
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Devuelve un `IUnknown` interfaz para el contexto del documento. Normalmente, el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz puede obtenerse a partir de este `IUnknown` interfaz.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Devuelve una cadena que contiene el CLSID de un visor personalizado, que normalmente se implementa mediante un evaluador de expresiones.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Devuelve un número de 32 bits que representa el número de ranura deseado si esta propiedad representa una dirección local del código administrado.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Devuelve una cadena que contiene la firma de la variable asociada con el objeto de propiedad.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
