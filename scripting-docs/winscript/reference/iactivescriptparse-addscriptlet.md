---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
Agrega un scriptlet de código al script.  Este método se utiliza en entornos donde entrelazan el estado persistente de script con el documento y del host es responsable de restaurar el script, en lugar de a través de una interfaz de `IPersist*` .  Los ejemplos primarios son los lenguajes de script HTML que permiten los scriptletes de código insertado en el documento HTML que se adjuntará a eventos intrínsecos \(por ejemplo, ONCLICK\= " button1.text\='Exit”\).  
  
## Sintaxis  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### Parámetros  
 `pstrDefaultName`  
 \[in\] dirección de un nombre predeterminado para asociar al scriptlet.  Si el scriptlet no contiene llamar información \(como en el ejemplo de ONCLICK arriba\), este nombre se utiliza para identificar el scriptlet.  Si este parámetro es `NULL`, el motor de script produce un nombre único, si es necesario.  
  
 `pstrCode`  
 \[in\] dirección del texto de scriptlet a agregar.  La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrItemName`  
 \[in\] la dirección de un búfer que contiene el nombre del elemento asociado a este scriptlet.  Este parámetro, además de `pstrSubItemName`, identifica el objeto para el que el scriptlet es un controlador de eventos.  
  
 `pstrSubItemName`  
 \[in\] dirección de un búfer que contiene el nombre de `subobject` de elemento al que está asociado este scriptlet; este nombre se debe encontrar en la información de tipo de elemento denominado.  Este parámetro es NULL si el scriptlet a asociar al elemento especificado en lugar de `subitem`.  Este parámetro, además de `pstrItemName`, identifica el objeto específico para el que el scriptlet es un controlador de eventos.  
  
 `pstrEventName`  
 \[in\] dirección de un búfer que contiene el nombre del evento para el que el scriptlet es un controlador de eventos.  
  
 `pstrDelimiter`  
 \[in\] dirección de delimitador de FIN\-de\- scriptlet.  Cuando el parámetro de `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final de scriptlet.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el fin de scriptlet.  
  
 `dwSourceContextCookie`  
 \[in\] valor definido por la aplicación que se utiliza para fines de depuración.  
  
 `ulStartingLineNumber`  
 \[in\] el valor Cero\- basado en que especifica que alinee el análisis se iniciará en.  
  
 `dwFlags`  
 \[in\] marcas asociados al scriptlet.  Puede ser una combinación de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|SCRIPTTEXT\_ISVISIBLE|Indica que el texto del script debe estar visible \(y, por consiguiente, accesible por nombre\) como método global en el espacio de nombres del script.|  
|SCRIPTTEXT\_ISPERSISTENT|Indica que el código agregado durante esta llamada debe guardarse si se guarda el motor de script \(por ejemplo, con una llamada a `IPersist*::Save`\), o si el motor de script se restaura por una transición al estado inicializado.  Para obtener más información sobre este estado, vea los estados del motor de script.|  
  
 `pbstrName` ,  
 \[out\] nombre real utilizado para identificar el scriptlet.  Éste es estar en orden de preferencia: un nombre explícitamente especificado en el texto del scriptlet, el nombre predeterminado en `pstrDefaultName`, o un nombre único sintetizado por el motor de script.  
  
 `pexcepinfo` ,  
 \[out\] dirección de una estructura que contiene la información de excepción.  Esta estructura se debería rellenar si se devuelve DISP\_E\_EXCEPTION.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`DISP_E_EXCEPTION`|Se ha producido una excepción en el análisis de scriptlet.  El parámetro de `pexcepinfo` contiene información sobre la excepción.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOTIMPL`|Este método no se admite; el motor de script no admite la adición evento\- que se recibe scriptletes.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\) y por tanto no se errónea.|  
|`OLESCRIPT_E_INVALIDNAME`|El nombre predeterminado proporcionado no es válido en este lenguaje de comandos.|  
|`OLESCRIPT_E_SYNTAX`|Un error de sintaxis sin especificar se produjo en el scriptlet.|  
  
## Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)