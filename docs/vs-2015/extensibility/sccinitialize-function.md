---
title: Función SccInitialize | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce52b65d028f82d75d4890b0b1298b4d13b7eafa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200036"
---
# <a name="sccinitialize-function"></a>SccInitialize (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función inicializa el complemento de control de código fuente y proporciona capacidades y límites al entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de El complemento de control de código fuente puede colocar un puntero a su estructura de contexto aquí.  
  
 `hWnd`  
 de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 `lpCallerName`  
 de Nombre del programa que llama al complemento de control de código fuente.  
  
 `lpSccName`  
 [in, out] Búfer en el que el complemento de control de código fuente coloca su propio nombre (no superar `SCC_NAME_LEN` ).  
  
 `lpSccCaps`  
 enuncia Devuelve las marcas de capacidad del complemento de control de código fuente.  
  
 `lpAuxPathLabel`  
 [in, out] Búfer en el que el complemento de control de código fuente coloca una cadena que describe el `lpAuxProjPath` parámetro devuelto por [SccOpenProject](../extensibility/sccopenproject-function.md) y [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (no se supera `SCC_AUXLABEL_LEN` ).  
  
 `pnCheckoutCommentLen`  
 enuncia Devuelve la longitud máxima permitida para un Comentario de desprotección.  
  
 `pnCommentLen`  
 enuncia Devuelve la longitud máxima permitida para otros comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Inicialización del control de código fuente correcta.|  
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema.|  
|SCC_E_NOTAUTHORIZED|No se permite al usuario realizar la operación especificada.|  
|SCC_E_NONSPECFICERROR|Error no específico; no se inicializó el sistema de control de código fuente.|  
  
## <a name="remarks"></a>Observaciones  
 El IDE llama a esta función cuando se carga por primera vez el complemento de control de código fuente. Permite al IDE pasar determinada información, como el nombre del autor de la llamada, al complemento. El IDE también recibe cierta información como la longitud máxima permitida para los comentarios y las capacidades del complemento.  
  
 `ppvContext`Apunta a un `NULL` puntero. El complemento de control de código fuente puede asignar una estructura para su propio uso y almacenar un puntero a esa estructura en `ppvContext` . El IDE pasará este puntero a todas las demás funciones de la API de VSSCI, lo que permite que el complemento tenga información de contexto disponible sin tener que recurrir al almacenamiento global y admitir varias instancias del complemento. Esta estructura debe desasignarse cuando se llama a [SccUninitialize](../extensibility/sccuninitialize-function.md) .  
  
 Los `lpCallerName` `lpSccName` parámetros y permiten que el IDE y el complemento de control de código fuente intercambien los nombres. Estos nombres se pueden usar simplemente para distinguir entre varias instancias o, en realidad, pueden aparecer en menús o cuadros de diálogo.  
  
 El `lpAuxPathLabel` parámetro es una cadena que se usa como comentario para identificar la ruta de acceso del proyecto auxiliar que se almacena en el archivo de solución y que se pasa al complemento de control de código fuente en una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../includes/vsvss-md.md)] usa la cadena "proyecto de SourceSafe:"; otros complementos de control de código fuente deben abstenerse de usar esta cadena concreta.  
  
 El `lpSccCaps` parámetro proporciona al complemento de control de código fuente un lugar donde almacenar marcadores que indica las capacidades del complemento. (Para obtener una lista completa de las marcadores de capacidad, consulte [marcas de capacidad](../extensibility/capability-flags.md)). Por ejemplo, si el complemento planea escribir los resultados en una función de devolución de llamada proporcionada por el llamador, el complemento establecería el bit de funcionalidad SCC_CAP_TEXTOUT. Esto indicaría al IDE que creara una ventana para los resultados del control de versiones.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Marcas de capacidad](../extensibility/capability-flags.md)
