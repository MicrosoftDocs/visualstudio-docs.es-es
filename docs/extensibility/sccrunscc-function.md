---
title: "SccRunScc (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc (función)"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccRunScc (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función invoca la herramienta de administración de control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 \[in\] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Matriz de nombres de archivo seleccionados.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Se invocó correctamente la herramienta de administración de control de código fuente.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación.|  
|SCC\_E\_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención.|  
|SCC\_E\_CONNECTIONFAILURE|No se pudo conectar al sistema de control de código fuente.|  
|SCC\_E\_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 Esta función permite al llamador tener acceso a la gama completa de características del sistema de control de código fuente a través de una herramienta de administración externo. Si el sistema de control de código fuente no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar funciones de administración necesarios.  
  
 Esta función se invoca con un número y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, la lista de archivos puede utilizarse para preseleccionar archivos en la interfaz de administración; de lo contrario, puede omitir la lista.  
  
 Esta función normalmente se invoca cuando el usuario selecciona el **Inicio \< servidor de Control de código fuente \>** desde el **archivo** \-\> **Control de código fuente** menú. Esto **iniciar** opción de menú puede siempre deshabilitado o incluso ocultarse estableciendo una entrada del registro. Para obtener información más detallada, vea [Cómo: instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md). Esta función sólo se llama si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el `SCC_CAP_RUNSCC` bit de capacidad \(consulte [Marcadores de capacidad](../extensibility/capability-flags.md) para obtener más información sobre este y otros bits de capacidad\).  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Cómo: instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)