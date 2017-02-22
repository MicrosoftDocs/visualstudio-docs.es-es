---
title: "IDebugProgramPublisher2::PublishProgram | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::PublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::PublishProgram"
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::PublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método hace que un programa disponibles para los motores de depuración \(DEs\) y el administrador de depuración de la sesión.  
  
## Sintaxis  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```c#  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### Parámetros  
 `Engines`  
 \[in\]  Una matriz de GUID para el DES que puede iniciar o asociar a este programa.  
  
 `szFriendlyName`  
 \[in\]  Nombre descriptivo para el programa \(esto aparece en los menús o los cuadros de diálogo mostrados al usuario\).  
  
 `pDebuggeeInterface`  
 \[in\]  interfaz de `IUnknown` para el programa \(este valor se utiliza como una cookie para identificar el programa; este mismo valor es “unpublish usado” el programa\)  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para que un programa no está disponible para la depuración, llame a [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## Vea también  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)