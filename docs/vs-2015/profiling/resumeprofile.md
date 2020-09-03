---
title: ResumeProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 289aff1025570d0840eb4f0815b88d9023033a7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149256"
---
# <a name="resumeprofile"></a>ResumeProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El método `ResumeProfile` reduce el contador de suspensiones y reanudaciones para el nivel de generación de perfiles especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Level`  
  
 Indica el nivel de perfil al que se puede aplicar la recopilación de datos de rendimiento. Los enumeradores **PROFILE_CONTROL_LEVEL** siguientes se pueden usar para indicar uno de tres niveles en los que se puede aplicar la recopilación de datos de rendimiento:  
  
|Enumerador|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|La configuración de nivel global afecta a todos los procesos y subprocesos en la generación de perfiles.|  
|PROFILE_PROCESSLEVEL|La configuración de nivel de proceso afecta a todos los subprocesos que forman parte del proceso especificado.|  
|PROFILE_THREADLEVEL|La configuración de nivel de generación de perfiles de subproceso afecta al subproceso especificado.|  
  
 `dwId`  
  
 Identificador del proceso o subproceso que genera el sistema.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE_COMMAND_STATUS**. El valor devuelto puede ser cualquiera de los siguientes:  
  
|Enumerador|Description|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|El id. del elemento de generación de perfiles no existe.|  
|PROFILE_ERROR_LEVEL_NOEXIST|El nivel de generación de perfiles especificado no existe.|  
|PROFILE_ERROR_MODE_NEVER|El modo de generación de perfiles se estableció en NEVER cuando se llamó a la función.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Todavía no se ha implementado la llamada a la función de generación de perfiles, el nivel de generación de perfiles o la combinación de llamada y nivel.|  
|PROFILE_OK|La llamada se ha realizado correctamente.|  
  
## <a name="remarks"></a>Observaciones  
 El valor inicial del contador de suspensiones y reanudaciones es 0. Cada llamada a SuspendProfile suma 1 al recuento de suspensiones y reanudaciones; cada llamada a ResumeProfile resta 1.  
  
 Cuando el recuento de suspensiones y reanudaciones es mayor que 0, el estado de suspensión y reanudación para el nivel es OFF. Cuando el recuento es menor o igual que 0, el estado de suspensión y reanudación es ON.  
  
 Cuando el estado de inicios y paradas, y el estado de suspensión y reanudación son los dos ON, el estado de generación de perfiles para el nivel es ON. Para que se pueda generar el perfil de un subproceso, los estados de nivel global, de proceso y de subproceso para el subproceso deben ser ON.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Información de la función  
 Encabezado: declarado en VSPerf.h  
  
 Biblioteca de importación: VSPerf.lib  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función ResumeProfile. En el ejemplo se da por supuesto que se ha realizado una llamada al método SuspendProfile para el mismo subproceso o proceso identificado por [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)
