---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
Devuelve un enumerador de los contextos de expresión conocidos por este componente.  
  
## Sintaxis  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parámetros  
 `ppedec`  
 \[out\] un enumerador de los contextos de expresión conocidos por este componente.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El administrador de la depuración utiliza este método para buscar todos los contextos globales de la expresión asociados a un subproceso determinado.  
  
> [!NOTE]
>  Este método se llama en el subproceso de interés.  Depende del implementador para identificar el subproceso actual y devolver un enumerador adecuado.  
  
## Vea también  
 [IProvideExpressionContexts \(Interfaz\)](../../winscript/reference/iprovideexpressioncontexts-interface.md)