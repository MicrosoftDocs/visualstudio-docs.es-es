---
title: IDebugErrorEvent2::GetErrorMessage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dffd06c7342b77f1e4293d50217a0c6a468bf18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Devuelve información que permite la construcción de un mensaje de error legible para el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMessageType`  
 [out] Devuelve un valor de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeración, que describe el tipo de mensaje.  
  
 `pbstrErrorFormat`  
 [out] El formato del mensaje para el usuario final (vea "Comentarios" para obtener más información).  
  
 `hrErrorReason`  
 [out] Trata el código de error del mensaje.  
  
 `pdwType`  
 [out] Gravedad del error (use las constantes MB_XXX para `MessageBox`; por ejemplo, `MB_EXCLAMATION` o `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Ruta de acceso a un archivo de ayuda (establecida en un valor null si no hay ningún archivo de Ayuda).  
  
 `pdwHelpId`  
 [out] Identificador del tema de ayuda para mostrar (se establece en 0 si no hay ningún tema de Ayuda).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El mensaje de error se debe dar formato a lo largo de las líneas de `"What I was doing.  %1"`. El `"%1"` , a continuación, se reemplazaría por el llamador con el mensaje de error que se deriva el código de error (que se devuelve en `hrErrorReason`). El `pMessageType` parámetro indica que al llamador determinar cómo debe mostrarse el mensaje de error final.  
  
## <a name="see-also"></a>Vea también  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)