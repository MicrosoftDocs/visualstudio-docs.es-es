---
title: "Función SccInitialize | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccInitialize
helpviewer_keywords: SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6bf217218dcc1830cc2acf2833aa7e31e85745d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccinitialize-function"></a>SccInitialize (función)
Esta función inicializa el complemento de control de código fuente y proporciona capacidades y limitaciones para el entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppvContext`  
 [in] El complemento de control de código fuente puede colocar un puntero a su estructura de contexto aquí.  
  
 `hWnd`  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 `lpCallerName`  
 [in] El nombre del programa de llamada complemento del control de código fuente.  
  
 `lpSccName`  
 [entrada, salida] El búfer en el complemento de control de código fuente coloca su propio nombre (no debe superar `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Devuelve el control de código fuente marcadores de capacidad del complemento.  
  
 `lpAuxPathLabel`  
 [entrada, salida] El búfer en el complemento de control de código fuente coloca una cadena que describe la `lpAuxProjPath` parámetro devuelto por la [SccOpenProject](../extensibility/sccopenproject-function.md) y [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (no debe superar `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Devuelve la longitud máxima permitida para un comentario de desprotección.  
  
 `pnCommentLen`  
 [out] Devuelve la longitud máxima permitida para otros comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Inicialización de control de origen se realizó correctamente.|  
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar la operación especificada.|  
|SCC_E_NONSPECFICERROR|Error no determinado; no se inicializó el sistema de control de código fuente.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE llama a esta función cuando carga por primera vez el complemento de control de código fuente. Permite que el IDE para que se pase determinada información, como el nombre del autor de la llamada, en el complemento. El IDE también obtiene cierta información como la longitud máxima permitida para comentarios y capacidades del complemento.  
  
 El `ppvContext` apunta a un `NULL` puntero. Puede asignar una estructura para su propio uso y almacenar un puntero a esa estructura en el complemento de control de código fuente `ppvContext`. El IDE aprobará this (puntero) a cada función de API de VSSCI, lo que permite el complemento para que tenga información de contexto disponible sin tener que recurrir a almacenamiento global y para admitir varias instancias del complemento. Esta estructura debe desasignarse cuando la [SccUninitialize](../extensibility/sccuninitialize-function.md) se llama.  
  
 El `lpCallerName` y `lpSccName` parámetros permiten el IDE y el complemento de control de código fuente intercambiar los nombres. Estos nombres pueden utilizarse simplemente para distinguir entre varias instancias o realmente pueden aparecer en los menús o cuadros de diálogo.  
  
 El `lpAuxPathLabel` parámetro es una cadena que se utiliza como un comentario para identificar la ruta de acceso del proyecto auxiliar que se almacena en el archivo de solución y pasa el control de código fuente del complemento en una llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]utiliza la cadena "proyecto de SourceSafe:"; otros complementos de control de código fuente deben abstenerse de utilizar esta cadena concreta.  
  
 El `lpSccCaps` parámetro proporciona el control de código fuente complemento un lugar para almacenar los marcadores de bits que indica las capacidades del complemento. (Para obtener una lista completa de los marcadores de bits de capacidad, consulte [capacidad marcas](../extensibility/capability-flags.md)). Por ejemplo, si los planes de complemento para escribir resultados a una función de devolución de llamada proporcionada por el autor de la llamada, el complemento establecería la capacidad de bits SCC_CAP_TEXTOUT. Esto podría indicar el IDE para crear una ventana de resultados de control de versión.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)