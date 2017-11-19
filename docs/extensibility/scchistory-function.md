---
title: "Función SccHistory | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccHistory
helpviewer_keywords: SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93c32d9eaa3549529a649472550ec8268cd0f6e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="scchistory-function"></a>SccHistory (función)
Esta función muestra el historial de los archivos especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvContext`  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 `hWnd`  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 `nFiles`  
 [in] Número de archivos especificado en el `lpFileName` matriz.  
  
 `lpFileName`  
 [in] Matriz de nombres completos de los archivos.  
  
 `fOptions`  
 [in] Marcas de comando (actualmente no utilizados).  
  
 `pvOptions`  
 [in] Opciones de específicas del complemento de control de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Historial de versiones se obtuvo correctamente.|  
|SCC_I_RELOADFILE|El sistema de control de código fuente modificado realmente el archivo en el disco al capturar el historial (por ejemplo, obteniendo una versión anterior del mismo), por lo que el IDE debe volver a cargar este archivo.|  
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|  
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_PROJNOTOPEN|No ha sido el proyecto está abierto.|  
|SCC_E_NONSPECIFICERROR|Error no determinado. No se pudo obtener el historial de archivos.|  
  
## <a name="remarks"></a>Comentarios  
 El complemento de control de código fuente puede mostrar su propio cuadro de diálogo para mostrar el historial de cada archivo, utilizando `hWnd` como la ventana primaria. Como alternativa, el texto opcional salida devolución de llamada de función proporcionado a la [SccOpenProject](../extensibility/sccopenproject-function.md) pueden utilizarse, si es compatible.  
  
 Tenga en cuenta que en determinadas circunstancias, el archivo que se está examinando puede cambiar durante la ejecución de esta llamada. Por ejemplo, el [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando history proporciona al usuario una oportunidad para obtener una versión anterior del archivo. En tal caso, el origen de controlar el complemento devuelve `SCC_I_RELOAD` para advertir que el IDE que necesita volver a cargar el archivo.  
  
> [!NOTE]
>  Si el complemento de control de código fuente no admite esta función para una matriz de archivos, se puede mostrar solo el historial de archivos para el primer archivo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)