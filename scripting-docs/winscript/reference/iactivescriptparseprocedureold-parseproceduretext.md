---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
Analiza el procedimiento de código determinado y agregue un procedimiento anónimo al espacio de nombres.  
  
## Sintaxis  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### Parámetros  
 `pstrCode`  
 \[in\] texto de procedimiento Va a evaluar.  La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrFormalParams`  
 \[in\] nombres de parámetro de Formal para el procedimiento.  Los nombres de parámetro deben separarse con los delimitadores adecuados para el motor de script.  Los nombres no se deben agregar entre paréntesis.  
  
 `pstrItemName`  
 \[in\] nombre del elemento denominado que proporciona el contexto en el que el procedimiento debe ser evaluado.  Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de script.  
  
 `punkContext`  
 \[in\] objeto de contexto.  Este objeto se reserva para el uso en un entorno de depuración, donde por contexto se puede proporcionar el depurador para representar un contexto activo en tiempo de ejecución.  Si este parámetro es `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 \[in\] delimitador de FIN\-de\- procedimiento de El.  Cuando `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final del procedimiento.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún procesamiento condicional, primitivo \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 \[in\] valor definido por la aplicación que se utiliza para fines de depuración.  
  
 `ulStartingLineNumber`  
 \[in\] valor Cero\- basado en que especifica en qué línea iniciará el análisis.  
  
 `dwFlags`  
 \[in\] marcas asociadas al procedimiento.  Puede ser una combinación de estos valores.  
  
|Constante|Valor|Significado|  
|---------------|-----------|-----------------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|Indica que el código de `pstrCode` es una expresión que representa el valor devuelto del procedimiento.|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|Indica que el puntero de `this` se incluye en el ámbito de procedimiento.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|Indica que los elementos primarios del puntero de `this` están incluidos en el ámbito de procedimiento.|  
  
 `ppdisp`  
 \[out\] devuelve un contenedor de envío donde el procedimiento el método predeterminado analizado por este método.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_NOTIMPL`|Este método no es compatible.  El motor de script no admite la adición del tiempo de ejecución de procedimientos al espacio de nombres.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script está en el estado no inicializado o cerrado\).|  
|`OLESCRIPT_E_SYNTAX`|Un error de sintaxis sin especificar se produjo en el procedimiento.|  
|`S_FALSE`|El motor de script no admite un objeto de envío; el parámetro de `ppdisp`se establece en `NULL`.|  
  
## Comentarios  
 No se evalúa ningún script durante esta llamada; en su lugar, el procedimiento se compila en un método en `ppdisp` donde se puede llamar al script posterior.  
  
 Esta interfaz está desusada a favor de la interfaz de `IActiveScriptParseProcedure` .  El método de `IActiveScriptParseProcedure::ParseProcedureText` es similar a este método, pero que el nombre de procedimiento es especificado.  En todas las circunstancias, `IActiveScriptParseProcedure::ParseProcedureText` se debe utilizar.  
  
## Vea también  
 [IActiveScriptParseProcedureOld \(Interfaz\)](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)