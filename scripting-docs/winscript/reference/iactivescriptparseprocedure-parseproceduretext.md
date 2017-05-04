---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
Analiza el procedimiento de código determinado y agrega el procedimiento al espacio de nombres.  
  
## Sintaxis  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### Parámetros  
 `pstrCode`  
 \[in\] dirección del texto del procedimiento a evaluar.  La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrFormalParams`  
 \[in\] dirección de los nombres de parámetros formales del procedimiento.  Los nombres de parámetro deben separarse con los delimitadores adecuados para el motor de script.  Los nombres no se deben agregar entre paréntesis.  
  
 `pstrProcedureName`  
 \[in\] dirección del nombre del procedimiento que se va a analizar.  
  
 `pstrItemName`  
 \[in\] dirección de nombre de elemento que proporciona el contexto en el que el procedimiento debe ser evaluado.  Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de script.  
  
 `punkContext`  
 \[in\] dirección del objeto de contexto.  Este objeto se reserva para el uso en un entorno de depuración, donde por contexto se puede proporcionar el depurador para representar un contexto activo en tiempo de ejecución.  Si este parámetro es `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 \[in\] dirección de delimitador de FIN\-de\- procedimiento.  Cuando `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final del procedimiento.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 \[in\] valor definido por la aplicación que se utiliza para fines de depuración.  
  
 `ulStartingLineNumber`  
 \[in\] el valor Cero\- basado en que especifica que alinee el análisis se iniciará en.  
  
 `dwFlags`  
 \[in\] marcas asociadas al procedimiento.  Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTPROC\_ISEXPRESSION|Indica que el código de `pstrCode` es una expresión que representa el valor devuelto del procedimiento.  De forma predeterminada, el código puede contener una expresión, una lista de extractos, o cualquier otra cosa permite en un procedimiento por el lenguaje de scripting.|  
|SCRIPTPROC\_IMPLICIT\_THIS|Indica que el puntero de `this` se incluye en el ámbito de procedimiento.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|Indica que los elementos primarios del puntero de `this` están incluidos en el ámbito de procedimiento.|  
  
 `ppdisp`  
 \[out\] dirección el puntero para el objeto que contiene los métodos globales y las propiedades del script.  Si el motor de script no admite este tipo de objeto, se devuelve `NULL` .  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_NOTIMPL`|Este método no es compatible.  El motor de script no admite la adición del tiempo de ejecución de procedimientos al espacio de nombres.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script está en el estado no inicializado o cerrado\).|  
|`OLESCRIPT_E_SYNTAX`|Un error de sintaxis sin especificar se produjo en el procedimiento.|  
|`S_FALSE`|El motor de script no admite un objeto de envío; el parámetro de `ppdisp` se establece en `NULL`.|  
  
## Comentarios  
 No se evalúa ningún script durante esta llamada; en su lugar, el procedimiento se compila en el script donde se puede llamar al script posterior.  
  
## Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)