---
title: Función SccRunScc | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 322ebe148144260106fb895273b66e1b9f5696f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccrunscc-function"></a>SccRunScc (función)
Esta función invoca la herramienta de administración de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos especificado en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de archivo seleccionados.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Se invocó correctamente la herramienta de administración de control de código fuente.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación.|  
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_CONNECTIONFAILURE|No se pudo conectar con el sistema de control de código fuente.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_NONSPECIFICERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función permite que el llamador tener acceso a la amplia gama de características del sistema de control de código fuente mediante una herramienta de administración externo. Si el sistema de control de código fuente no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para llevar a cabo funciones de administración necesarios.  
  
 Esta función se invoca con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, la lista de archivos puede utilizarse para archivos de la interfaz de administración de antemano en caso contrario, se puede omitir la lista.  
  
 Esta función normalmente se invoca cuando el usuario selecciona el **iniciar \<servidor de Control de origen >** desde el **archivo** -> **Control de código fuente** menú. Esto **iniciar** opción de menú puede siempre deshabilitada o incluso los ocultos mediante el establecimiento de una entrada del registro. Vea [Cómo: instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obtener más información. Esta función se invoca únicamente si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el `SCC_CAP_RUNSCC` bit de capacidad (vea [capacidad marcas](../extensibility/capability-flags.md) para obtener detalles sobre este y otros elementos de la capacidad).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Cómo: instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Marcas de capacidad](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)