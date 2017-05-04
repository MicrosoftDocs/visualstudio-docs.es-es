---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
Devuelve un intervalo de caracteres que se agregaron utilizando el método de `IDebugDocumentHelper::AddDeferredText` , en el documento de host original.  
  
## Sintaxis  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parámetros  
 `dwTextStartCookie`  
 \[in\] cookie Host\- definido que representa la posición inicial del texto.  
  
 `pcharText`  
 \[in, out\] búfer de texto de caracteres de A.  Este método no devuelve los caracteres si este parámetro es `NULL`.  
  
 `pstaTextAttr`  
 \[in, out\] búfer de atributo de carácter de A.  Este método no devuelve atributos si este parámetro es `NULL`.  
  
 `pcNumChars`  
 \[in, out\] Indica el número de caracteres o los atributos reales devueltos.  Este parámetro se debe establecer en cero antes de llamar a este método.  
  
 `cMaxChars`  
 \[in\] número de caracteres máximo de Va a devolver.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|Este método no está implementado.|  
  
## Comentarios  
 Este método puede devolver `E_NOTIMPL`, si el host no llama a `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Este método devuelve el texto del documento original.  El host no realiza un seguimiento de ediciones u otros cambios en el documento.  
  
## Vea también  
 [IDebugDocumentHost \(Interfaz\)](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)