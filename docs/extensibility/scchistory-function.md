---
title: "SccHistory (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory (función)"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccHistory (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función muestra el historial de los archivos especificados.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parámetros  
 `pvContext`  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 `hWnd`  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 `nFiles`  
 \[in\] Número de archivos especificado en el `lpFileName` matriz.  
  
 `lpFileName`  
 \[in\] Matriz de nombres completos de los archivos.  
  
 `fOptions`  
 \[in\] Indicadores de comando \(actualmente no utilizados\).  
  
 `pvOptions`  
 \[in\] Opciones específicas del complemento de control de código fuente.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Historial de versiones se obtuvo correctamente.|  
|SCC\_I\_RELOADFILE|El sistema de control de código fuente modificado realmente el archivo en el disco al capturar el historial \(por ejemplo, al obtener una versión anterior del mismo\), por lo que el IDE debe cargar este archivo.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC\_E\_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_PROJNOTOPEN|El proyecto no ha sido abierto.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico. No se pudo obtener el historial de archivos.|  
  
## Comentarios  
 El complemento de control de código fuente puede mostrar su propio cuadro de diálogo para mostrar el historial de cada archivo, utilizando `hWnd` como la ventana primaria. Como alternativa, devolución de llamada de salida de texto opcional función proporcionado a la [SccOpenProject](../extensibility/sccopenproject-function.md) puede utilizarse si es compatible.  
  
 Tenga en cuenta que, en determinadas circunstancias, el archivo que se está examinando puede cambiar durante la ejecución de esta llamada. Por ejemplo, el [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando history proporciona al usuario una oportunidad para obtener una versión anterior del archivo. En tal caso, el origen de controlar el complemento devuelve `SCC_I_RELOAD` para advertir que el IDE que debe volver a cargar el archivo.  
  
> [!NOTE]
>  Si el complemento de control de código fuente no admite esta función para una matriz de archivos, se puede mostrar el historial de archivos para el primer archivo.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)