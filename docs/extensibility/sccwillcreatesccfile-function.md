---
title: "SccWillCreateSccFile (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile (función)"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccWillCreateSccFile (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función determina si el complemento de control de código fuente admite la creación de la MSSCCPRJ. Archivos SCC para cada uno de los archivos determinados.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 \[in\] El número de nombres de archivo que se incluye en el `lpFileNames` de matriz, así como la longitud de la `pbSccFiles` matriz.  
  
 lpFileNames  
 \[in\] Una matriz de nombres de archivo completo para comprobar \(matriz debe ser asignada por llamador\).  
  
 pbSccFiles  
 \[entrada, salida\] Matriz en la que se va a almacenar los resultados.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Correcto.|  
|SCC\_E\_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 Esta función se invoca con una lista de archivos para determinar si el complemento de control de código fuente proporciona compatibilidad en el MSSCCPRJ. Archivo de control de código fuente para cada uno de los archivos determinados \(para obtener más información sobre la MSSCCPRJ. Archivo de control de código fuente, consulte [MSSCCPRJ. Archivo de control de código fuente](../extensibility/mssccprj-scc-file.md)\). Pueden declarar los complementos de control de código fuente si disponen de la capacidad de crear MSSCCPRJ. Archivos SCC declarando `SCC_CAP_SCCFILE` durante la inicialización. El complemento devuelve `TRUE` o `FALSE` por cada archivo en el `pbSccFiles` matriz para indicar cuál de los archivos determinados tiene MSSCCPRJ. Compatibilidad con el control de código fuente. Si el complemento devuelve un código correcto de la función, se respetan los valores de la matriz de devolución. En caso de error, se omite la matriz.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. Archivo de control de código fuente](../extensibility/mssccprj-scc-file.md)