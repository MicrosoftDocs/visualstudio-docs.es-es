---
title: "IActiveScriptParse::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_ParseScriptText"
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptParse::ParseScriptText
Analiza el scriptlet de código dado, agregando declaraciones al espacio de nombres y evaluando código según corresponda.  
  
## Sintaxis  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### Parámetros  
  
|||  
|-|-|  
|`pstrCode`|\[in\] Dirección del texto de scriptlet a evaluar.  La interpretación de esta cadena depende del lenguaje de scripting.|  
|`pstrItemName`|\[in\] Dirección de nombre de elemento que proporciona el contexto en el que se va a evaluar el scriptlet.  Si este parámetro es NULL, el código se evalúa en el contexto global del motor de scripting.|  
|`punkContext`|\[in\] Dirección del objeto de contexto.  Este objeto se reserva para utilizarlo en un entorno de depuración, donde el depurador puede proporcionar tal contexto para representar un contexto activo en tiempo de ejecución.  Si este parámetro es NULL, el motor utiliza `pstrItemName` para identificar el contexto.|  
|`pstrDelimiter`|\[in\] Dirección del delimitador de fin de scriptlet.  Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas sencillas \(''\), para detectar el final de scriptlet.  Este parámetro especifica el delimitador que el host utiliza, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazar una comilla sencilla \['\] con dos comillas sencillas para su uso como delimitador\).  Exactamente cómo \(y si\) el motor de scripting hace uso de esta información depende del motor de scripting.  Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el fin del scriptlet.|  
|`dwSourceContextCookie`|\[in\] Cookie utilizada para fines de depuración.|  
|`ulStartingLineNumber`|\[in\] Valor basado en cero que especifica en qué línea empezará el análisis.|  
|`dwFlags`|\[in\] Marcas asociadas al scriptlet.  Pueden ser una combinación de estos valores:|  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTTEXT\_ISEXPRESSION|Si la distinción entre una expresión computacional y una instrucción es importante pero sintácticamente ambigua en el lenguaje de script, este marcador especifica que el scriptlet debe interpretarse como expresión, en lugar de como una instrucción o lista de instrucciones.  De forma predeterminada, las instrucciones se asumen a menos que se pueda determinar la opción correcta a partir de la sintaxis de texto del scriptlet.|  
|SCRIPTTEXT\_ISPERSISTENT|Indica que el código agregado durante esta llamada debe guardarse si se guarda el motor de scripting \(por ejemplo, a través de una llamada a `IPersist*::Save`\), o si el motor de scripting se restablece por medio de una transición de vuelta al estado inicializado.|  
|SCRIPTTEXT\_ISVISIBLE|Indica que el texto de script debe estar visible \(y, por tanto, invocable por nombre\) como método global en el espacio de nombres del script.|  
  
|||  
|-|-|  
|`pvarResult`|\[out\] Dirección de un búfer que recibe los resultados del procesamiento del scriptlet o `NULL` si el llamador no espera ningún resultado \(es decir, el valor de SCRIPTTEXT\_ISEXPRESSION no está establecido\).|  
|`pexcepinfo`|\[out\] Dirección de una estructura que recibe información de excepción.  Se rellena esta estructura si `IActiveScriptParse::ParseScriptText` devuelve DISP\_E\_EXCEPTION.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se produjo una excepción en el procesamiento del scriptlet.  El parámetro `pexcepinfo` contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_NOTIMPL`|Este método no es compatible.  El motor de scripting no admite evaluación en tiempo de ejecución de expresiones o instrucciones.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de scripting está en estado no inicializado o cerrado, o bien se estableció la marca SCRIPTTEXT\_ISEXPRESSION y el motor de scripting está en estado inicializado\).|  
|`OLESCRIPT_E_SYNTAX`|Un error de sintaxis sin especificar se produjo en el scriptlet.|  
  
## Comentarios  
 Si el motor de scripting se encuentra en estado inicializado, no se evaluará ningún código realmente durante esta llamada; en su lugar, tal código se pone en cola y se ejecuta cuando el motor de scripting realiza la transición \(o pasa\) al estado iniciado.  Dado que la ejecución no se permite en el estado inicializado, es un error llamar a este método con el indicador SCRIPTTEXT\_ISEXPRESSION cuando está en el estado inicializado.  
  
 El scriptlet puede ser una expresión, una lista de instrucciones todo lo permitido por el lenguaje de scripts.  Por ejemplo, este método se usa en la evaluación de la etiqueta \<SCRIPT\> HTML, que permite que las instrucciones se puedan ejecutar como la página HTML que se está construyendo, en lugar de simplemente compilarlas en el estado de script.  
  
 El código pasado a este método debe ser una parte del código válida y completa.  Por ejemplo, en VBScript no es válido llamar a este método una vez con Sub Function\(x\) y una segunda vez con `End Sub`.  El analizador no debe esperar la segunda llamada para completar la subrutina sino que en su lugar debe generar un error de análisis porque se inició una declaración de subrutina pero no se completó.  
  
 Para obtener más información sobre los estados de scripts, vea la sección sobre los estados del motor de script de [Motores Windows Script](../../winscript/windows-script-engines.md).  
  
## Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)