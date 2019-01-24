---
title: SccGetCommandOptions (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4237b967e63e89890bba5bed157ff98e7898a115
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823505"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (función)
Esta función pide al usuario para las opciones avanzadas para un comando determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 iCommand  
 [in] El comando para el que se solicitan las opciones avanzadas (consulte [comando código](../extensibility/command-code-enumerator.md) posibles valores).  
  
 ppvOptions  
 [in] La estructura de opción (también puede ser `NULL`).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_I_ADV_SUPPORT|El complemento de control de origen es compatible con las opciones avanzadas para el comando.|  
|SCC_I_OPERATIONCANCELED|El usuario canceló el origen control del complemento **opciones** cuadro de diálogo.|  
|SCC_E_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|  
|SCC_E_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está desprotegido actualmente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE llama a esta función por primera vez con `ppvOptions` = `NULL` para determinar si el complemento de control de origen es compatible con la característica de opciones avanzadas para el comando especificado. Si el complemento admite la característica para ese comando, el IDE llama a esta función nuevo cuando el usuario solicita las opciones avanzadas (normalmente se implementa como un **avanzadas** botón en un cuadro de diálogo) y proporciona un puntero no nulo para `ppvOptions` que apunta a un `NULL` puntero. El complemento almacena las opciones avanzadas, especificadas por el usuario en una estructura privada y devuelve un puntero a esa estructura en `ppvOptions`. Esta estructura se pasa a todas las demás funciones de API de complemento de Control de origen que necesitan saber sobre ella, incluidas las llamadas posteriores a la `SccGetCommandOptions` función.  
  
 Un ejemplo puede ayudar a aclarar esta situación.  
  
 Un usuario elige el **obtener** comando y el IDE muestra un **obtener** cuadro de diálogo. Las llamadas IDE el `SccGetCommandOptions` funcionando con `iCommand` establecido en `SCC_COMMAND_GET` y `ppvOptions` establecido en `NULL`. Esto se interpreta por el control de código fuente complemento como la pregunta, "¿tiene las opciones avanzadas pertinentes para este comando?" Si el complemento devuelve `SCC_I_ADV_SUPPORT`, el IDE muestra un **avanzadas** botón en su **obtener** cuadro de diálogo.  
  
 La primera vez que el usuario hace clic en el **avanzadas** botón, el IDE llama de nuevo el `SccGetCommandOptions` funcionar, esta vez con una que no sean de`NULL``ppvOptions` que apunta a un `NULL` puntero. El complemento se muestra su propia **opciones obtenga** cuadro de diálogo pide al usuario para obtener información, coloca dicha información en su propia estructura y devuelve un puntero a esa estructura en `ppvOptions`.  
  
 Si el usuario hace clic **avanzadas** en el mismo cuadro de diálogo, el IDE llama de nuevo el `SccGetCommandOptions` función nuevo sin cambiar `ppvOptions`, de modo que la estructura se pasa al complemento. Esto permite que el complemento reinicializar el cuadro de diálogo a los valores que el usuario haya establecido anteriormente. El complemento modifica la estructura en su lugar antes de devolver.  
  
 Por último, cuando el usuario hace clic en **Aceptar** en el IDE **obtener** cuadro de diálogo, las llamadas IDE el [SccGet](../extensibility/sccget-function.md), pasando la estructura devuelta en `ppvOptions` que contiene el Opciones avanzadas.  
  
> [!NOTE]
>  El comando `SCC_COMMAND_OPTIONS` se usa cuando el IDE muestra un **opciones** cuadro de diálogo que permite al usuario establece las preferencias que controlan cómo funciona la integración. Si desea que el complemento de control de origen proporcionar su propio cuadro de diálogo Preferencias, puede mostrar desde una **avanzadas** botón en el cuadro de diálogo de preferencias del IDE. El complemento es únicamente responsable de obtener y almacenar esta información; el IDE no usa ni modificarlo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)