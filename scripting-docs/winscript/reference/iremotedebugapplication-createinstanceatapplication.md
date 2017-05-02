---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
Permite la creación de objetos en el proceso de aplicación con código que es hacia fuera\-de\- proceso a la aplicación.  
  
## Sintaxis  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### Parámetros  
 `rclsid`  
 \[in\] identificador de clase \(CLSID\) del objeto creado.  
  
 `pUnkOuter`  
 \[in\] si `NULL`, el objeto no se crea como parte de un agregado.  Si no, `pUnkOuter` es un puntero a la interfaz de `IUnknown` del objeto global \( `IUnknown`que controla\).  
  
 `dwClsContext`  
 \[in\] contexto para ejecutar código del ejecutable.  Los valores se toman de la enumeración `CLSCTX`.  
  
 `riid`  
 \[in\] identificador de interfaz se utiliza para comunicarse con el objeto.  
  
 `ppvObject`  
 \[out\] Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en `riid`.  Sobre retorno correcto, \*`ppvObject` contiene el puntero solicitado de la interfaz.  Sobre el error, \*`ppvObject` contiene `NULL`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Delegados de este método a `CoCreateInstance`.  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)