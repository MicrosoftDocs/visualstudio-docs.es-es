---
title: "StopProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StopProfile"
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# StopProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La función `StopProfile` establece el contador en 0 \(desactivado\) para el nivel de generación de perfiles especificado.  
  
## Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### Parámetros  
 `Level`  
  
 Indica el nivel de perfil al que se puede aplicar la recolección de datos de rendimiento.  Los enumeradores **PROFILE\_CONTROL\_LEVEL** siguientes se pueden utilizar para indicar uno de los tres niveles a los que se puede aplicar la recolección de datos de rendimiento:  
  
|Enumerator|Descripción|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|La configuración de nivel global afecta a todos los procesos y subprocesos de la ejecución de generación de perfiles.|  
|PROFILE\_PROCESSLEVEL|La configuración de nivel de proceso afecta a todos los subprocesos que forman parte del proceso especificado.|  
|PROFILE\_THREADLEVEL|La configuración de nivel de subprocesos de la generación de perfiles afecta al subproceso especificado.|  
  
 `dwId`  
  
 Identificador del proceso o del subproceso generado por el sistema.  
  
## Valor de propiedad y valor devuelto  
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE\_COMMAND\_STATUS**.  El valor devuelto puede ser cualquiera de los siguientes:  
  
|Enumerator|Descripción|  
|----------------|-----------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|El Id. del elemento de generación de perfiles no existe.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|El nivel de generación de perfiles especificado no existe.|  
|PROFILE\_ERROR\_MODE\_NEVER|El modo de generación de perfiles se estableció en NEVER cuando se llamó a la función.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|Todavía no se ha implementado la llamada a la función de generación de perfiles, el nivel de generación de perfiles o la combinación de llamada y nivel.|  
|PROFILE\_OK|La llamada se realizó correctamente.|  
  
## Comentarios  
 StartProfile y StopProfile controlan el estado de Start\/Stop del nivel de generación de perfiles.  El valor predeterminado de Start\/Stop es 1.  El valor inicial se puede cambiar en el Registro.  Cada llamada a StartProfile establece el estado de Start\/Stop en 1; cada llamada a StopProfile lo establece en 0.  
  
 Cuando el valor del contador Start\/Stop es mayor que 0, el estado de Start\/Stop del nivel es ON.  Cuando es menor o igual que 0, el estado de Start\/Stop es OFF.  
  
 Cuando los estados de Start\/Stop y de Suspend\/Resume son ON, el estado de generación de perfiles del nivel es ON.  Para que se generen los perfiles de un subproceso los estados del subproceso en todos los niveles \(global, de proceso y de subproceso\) deben ser ON.  
  
## Equivalente en .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Información de la función  
 Encabezado: Declarado en VSPerf.h  
  
 Biblioteca de importación: VSPerf.lib  
  
## Ejemplo  
 En el siguiente ejemplo se ilustra el método StopProfile.  En el ejemplo se asume que se ha realizado una llamada al método StartProfile para el mismo subproceso o proceso identificado por [PROFILE\_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseStopProfile()  
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
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)