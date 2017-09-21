---
title: "SccDirQueryInfo (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo (función)"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccDirQueryInfo (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función examina una lista de directorios completos de su estado actual.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 nDirs  
 \[in\] El número de directorios seleccionado que se va a consultar.  
  
 lpDirNames  
 \[in\] Una matriz de rutas de acceso completas de los directorios que se desean consultar.  
  
 lpStatus  
 \[entrada, salida\] Una estructura de matriz para el complemento para devolver los indicadores de estado de control de código fuente \(consulte [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md) para obtener más información\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La consulta fue correcta.|  
|SCC\_E\_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 La función rellena la matriz devuelta con una máscara de bits de la `SCC_DIRSTATUS` familia \(consulte [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)\), una entrada para cada directorio dado. La matriz de estados está asignada por el llamador.  
  
 El IDE utiliza esta función antes de que se cambia el nombre de un directorio para comprobar si el directorio está bajo control de código fuente mediante una consulta si tiene un proyecto correspondiente. Si el directorio no está bajo control de código fuente, el IDE puede proporcionar la advertencia adecuada para el usuario.  
  
> [!NOTE]
>  Si elige no implementar uno o varios de los valores de estado de un complemento de control de código fuente, bits no está implementados se deben establecer en cero.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de estado de directorio](../extensibility/directory-status-code-enumerator.md)