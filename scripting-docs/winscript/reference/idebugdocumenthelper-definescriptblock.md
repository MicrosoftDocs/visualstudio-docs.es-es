---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
Indica a la aplicación auxiliar que un intervalo determinado de caracteres es un bloque de script que controla el motor de scripts especificado.  
  
## Sintaxis  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### Parámetros  
 `ulCharOffset`  
 \[in\] ubicación de inicio del bloque de script.  
  
 `cChars`  
 \[in\] número de caracteres del bloque de script.  
  
 `pas`  
 \[in\] motor de script para obtener este bloque de script.  
  
 `fScriptlet`  
 \[in\] marca que indica si el bloque de script es un scriptlet.  
  
 `pdwSourceContext`  
 \[out\] contexto de origen para obtener el bloque de script.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un host inteligente puede usar este método cuando los documentos contienen bloques incrustados del script.  Un motor de lenguaje puede usar este método cuando el código contiene scripts incrustados para otros lenguajes.  
  
 El motor de scripts es responsable de todas las búsquedas de contexto de color y código de sintaxis en el bloque de script.  
  
 El método de `DefineScriptBlock` debe llamar una vez agregado el texto \(por ejemplo, mediante el método de `IDebugDocumentHelper::AddDBCSText` \) pero antes de que se ha analizado el bloque de script \(por ejemplo, mediante el método de `IActiveScriptParse ::ParseScriptText` \).  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)