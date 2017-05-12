---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
El método de `Init` inicializa una aplicación auxiliar de depuración con un nombre y atributos inicial.  
  
## Sintaxis  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### Parámetros  
 `pda`  
 \[in\] aplicación de depuración se asociada a este documento.  
  
 `pszShortName`  
 \[in\] cadena terminada en null que contiene el nombre corto del documento.  
  
 `pszLongName`  
 \[in\] cadena terminada en null que contiene el nombre largo de archivo del documento.  
  
 `docAttr`  
 \[in\] especifica atributos de documento de texto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método inicializa una aplicación auxiliar de depuración con un nombre y atributos inicial.  
  
 Este documento no aparece en el árbol hasta que se llame a `IDebugDocumentHelper::Attach` .  
  
## Vea también  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR \(Constantes\)](../../winscript/reference/text-doc-attr-constants.md)