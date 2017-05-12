---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::CreateInstanceAtDebugger"
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::CreateInstanceAtDebugger
Permite la creación de objetos en el proceso del depurador por el código sea hacia fuera\-de\- proceso el depurador.  
  
> [!IMPORTANT]
>  Este método no debe ser implementado, porque permite que el código que no es de confianza cree objetos arbitrarios en un subproceso del depurador.  
  
## Sintaxis  
  
```  
HRESULT CreateInstanceAtDebugger(  
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
  
 No se implementa el método actualmente.  
  
## Vea también  
 [IApplicationDebugger \(Interfaz\)](../../winscript/reference/iapplicationdebugger-interface.md)