---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gets extendidas información para la propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### Parámetros  
 `guidExtendedInfo`  
 \[in\]  GUID que determina el tipo de información extendida que se va a recuperar.  Vea las notas de detalles.  
  
 `pExtendedInfo`  
 \[out\]  Devuelve `VARIANT` \(C\+\+\) o el objeto \(C\#\) que se pueden utilizar para recuperar información extendida de la propiedad.  Por ejemplo, este parámetro podría devolver una interfaz de `IUnknown` que se puede consultar una interfaz de [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) .  Vea las notas de detalles.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  devuelve `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` si no hay información extendida a recuperar.  
  
## Comentarios  
 Este método existe con el fin de recuperar información que no se presta a recuperar llamando al método de [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
 El GUID siguiente se reconoce normalmente con este método \(los valores de GUID se especifican para C\# como el nombre no está disponible en ningún ensamblado\).  GUID adicional se pueden crear para uso interno.  
  
|Name|GUID|Descripción|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2}|Devuelve una interfaz de `IUnknown` al documento.  Normalmente, la interfaz de [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) se puede obtener de esta interfaz de `IUnknown` .|  
|guidCodeContext|{e2fc65e\-56ce\-11d1\-b528\-00aax004a8797}|Devuelve una interfaz de `IUnknown` al contexto del documento.  Normalmente, la interfaz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) se puede obtener de esta interfaz de `IUnknown` .|  
|guidCustomViewerSupported|{d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c}|Devuelve una cadena que contiene el CLSID de un visor personalizado, implementado normalmente por un evaluador de expresiones.|  
|guidExtendedInfoSlot|{6df235ad\-82c6\-4292\-9c97\-7389770bc42f}|Devuelve un número de 32 bits que representa el número de ranura deseado si esta propiedad representa una dirección local de código administrado.|  
|guidExtendedInfoSignature|{b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd}|devuelve una cadena que contiene la firma de la variable asociado con el objeto de la propiedad.|  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)