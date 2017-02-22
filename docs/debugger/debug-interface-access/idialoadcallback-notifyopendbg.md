---
title: "IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback::NotifyOpenDBG (método)"
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyOpenDBG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se invoca cuando se ha abierto un archivo candidatos .dbg.  
  
## Sintaxis  
  
```cpp#  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### Parámetros  
 `dbgPath`  
 \[in\]  La ruta de acceso completa del archivo .dbg.  
  
 `resultCode`  
 \[in\]  Código que indica el éxito \(`S_OK`\) o el error de carga con respecto a este archivo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  El código devuelto se omite normalmente.  
  
## Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)