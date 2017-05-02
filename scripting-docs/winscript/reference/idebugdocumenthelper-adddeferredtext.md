---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
Notifica a la aplicación auxiliar que el texto determinado está disponible, pero no proporciona los caracteres.  
  
## Sintaxis  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### Parámetros  
 `cChars`  
 \[in\] número de caracteres \(Unicode\) a agregar.  
  
 `dwTextStartCookie`  
 \[in\] cookie Host\- definido que representa la posición inicial del texto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no.|  
  
## Comentarios  
 Este método permite el host difiera proporcionando los caracteres para agregar hasta que se necesitan, mientras que permite que la aplicación auxiliar generar notificaciones precisas y la información de tamaño.  El parámetro de `dwTextStartCookie` es una cookie, definida por el host, que representa la posición inicial del texto.  Las llamadas subsiguientes a `IDebugDocumentText::GetText` deben proporcionar esta cookie.  Por ejemplo, en un host que representa el texto de DBCS, ésta puede ser un desplazamiento de bytes.  
  
 Se supone que una única llamada a `IDebugDocumentText::GetText` puede obtener los caracteres de varias llamadas a `AddDeferredText`.  Las clases auxiliares también pueden ordenar el mismo intervalo de caracteres diferidos más de una vez.  
  
> [!NOTE]
>  Las llamadas a `AddDeferredText` no deben mezclar con llamadas a `AddUnicodeText` o a `AddDBCSText`.  Si ocurre esto, se devuelve `E_FAIL` .  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)