---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
Crea una expresión de depuración para el texto especificado.  
  
## Sintaxis  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### Parámetros  
 `pstrCode`  
 \[in\] proporciona el texto de la expresión o los extractos.  
  
 `nRadix`  
 \[in\] base a utilizar.  
  
 `pstrDelimiter`  
 \[in\] delimitador de FIN\-de\-script\- bloque en Bytes.  Cuando `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final del bloque de script.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 \[in\] la combinación de texto siguiente de depuración marca:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en un fragmento.  Este marcador puede afectar a la forma en que el texto es analizado por algunos lenguajes.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Si un valor devuelto está disponible, se utiliza el llamador.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|No permite los efectos secundarios.  Si se establece esta marca, la evaluación de la expresión no debe cambiar un estado de runtime.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Permite los puntos de interrupción durante la evaluación de texto.  Si este marcador no se establecer puntos de interrupción se omiten durante la evaluación de texto.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Permite informes de error durante la evaluación de texto.  Si este marcador no se establece los errores no se notifican al host durante la evaluación.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indica que se va a evaluar la expresión a un contexto del código en lugar de ejecutando la expresión propia|  
  
 `ppe`  
 \[out\] devuelve la expresión de depuración para el texto especificado.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea una expresión de depuración para el texto especificado.  
  
## Vea también  
 [IDebugExpressionContext \(Interfaz\)](../../winscript/reference/idebugexpressioncontext-interface.md)