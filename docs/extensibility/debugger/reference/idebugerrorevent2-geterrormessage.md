---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve información que permite la construcción de un mensaje de error legible.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### Parámetros  
 `pMessageType`  
 \[out\]  Devuelve un valor de enumeración de [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , describe el tipo de mensaje.  
  
 `pbstrErrorFormat`  
 \[out\]  El formato de mensaje final al usuario \(vea la sección “notas” para obtener detalles\).  
  
 `hrErrorReason`  
 \[out\]  El código de error el mensaje está sobre.  
  
 `pdwType`  
 \[out\]  Gravedad del error \(utilice constantes de MB\_XXX para `MessageBox`; por ejemplo, `MB_EXCLAMATION` o `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[out\]  Ruta de acceso a un archivo de ayuda \(se establece en un valor NULL si no hay ningún archivo de ayuda\).  
  
 `pdwHelpId`  
 \[out\]  Identificador del tema de Ayuda a mostrar \(se establece en 0 si no hay un tema de Ayuda\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 el mensaje de error se debe dar formato a lo largo de las líneas de `"What I was doing.  %1"`.  `"%1"` continuación se reemplaza por el llamador con el mensaje de error derivado del código de error \(que se devuelve en `hrErrorReason`\).  El parámetro de `pMessageType` indica a llamador cómo el mensaje de error final debe mostrar.  
  
## Vea también  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)