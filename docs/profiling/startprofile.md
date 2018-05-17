---
title: StartProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4de525650c7e93497c86fa7ebf493922d8fad6ef
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="startprofile"></a>StartProfile
La función `StartProfile` establece el contador en 1 (activado) para el nivel de generación de perfiles especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Level`  
  
 Indica el nivel de perfil en el que se puede aplicar la recopilación de datos de rendimiento. Los enumeradores **PROFILE_CONTROL_LEVEL** siguientes se pueden usar para indicar uno de tres niveles en los que se puede aplicar la recopilación de datos de rendimiento:  
  
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
  
## <a name="remarks"></a>Comentarios  
 StartProfile y StopProfile controlan el estado de Iniciar/Detener del nivel de generación de perfiles. El valor predeterminado de Iniciar/Detener es 1. El valor inicial se puede cambiar en el Registro. Cada llamada a StartProfile establece Iniciar/Detener en 1; cada llamada a StopProfile lo establece en 0.  
  
 Cuando el valor de Iniciar/Detener es mayor que 0, el estado de Iniciar/Detener del nivel es Activado. Cuando es menor o igual que 0, el estado de Iniciar/Detener es Desactivado.  
  
 Cuando el estado de Iniciar/Detener y de Suspensión/Reanudación es Activado, el estado de generación de perfiles para el nivel es Activado. Para que se pueda generar el perfil de un subproceso, el estado de nivel global, de proceso y de subproceso para el subproceso debe ser Activado.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Información de la función  
 Encabezado: declarado en VSPerf.h  
  
 Biblioteca de importación: VSPerf.lib  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la llamada de función StartProfile.  
  
```cpp  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)