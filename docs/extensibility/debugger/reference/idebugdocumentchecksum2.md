---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugDocumentChecksum2"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.  
  
## Sintaxis  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se puede implementar por cualquier componente que expone la interfaz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  Sin embargo, se implementa principalmente los motores de depuración para poder pasarse al IDE y utilizar la suma de comprobación inline en un archivo de símbolos \(\*.pdb\) al buscar un origen.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugDocumentChecksum2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera el identificador de la suma de comprobación y el algoritmo de documento dado el número de bytes máximo para utilizar.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll