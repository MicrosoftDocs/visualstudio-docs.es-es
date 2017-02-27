---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "Estructura MODULE_INFO"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe un módulo set \(DLL, EXE, o ensamblado\).  
  
## Sintaxis  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## Members  
 dwValidFields  
 Una combinación de marcadores de enumeración de [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) que especifica se completan los campos.  
  
 m\_bstrName  
 Nombre del módulo.  
  
 m\_bstrUrl  
 La dirección URL del módulo.  
  
 m\_bstrVersion  
 La versión del módulo.  
  
 m\_bstrDebugMessage  
 Un mensaje opcional sobre el módulo, por ejemplo, “Símbolos no puede cargarse”.  
  
 m\_addrLoadAddress  
 la dirección de la carga de módulos.  
  
 m\_addrPreferredLoadAddress  
 La dirección preferida de carga del módulo.  
  
 m\_dwSize  
 El tamaño del módulo.  
  
 m\_dwLoadOrder  
 El orden de carga de módulos.  
  
 m\_TimeStamp  
 Tiempo el archivo de símbolos se modificó.  
  
 m\_bstrUrlSymbolLocation  
 La ubicación del archivo de símbolos \(por ejemplo, “.  \\ "\) especificado en el módulo.  Utilizado como ubicación inicial para encontrar los símbolos para un módulo.  
  
 m\_dwModuleFlags  
 Una combinación de marcadores de enumeración de [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) que describe el módulo.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) donde se completa.  
  
 Esta estructura corresponde a cada módulo de la ventana de **Módulos** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)