---
title: "SuspendProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SuspendProfile"
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SuspendProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método `SuspendProfile` incrementa el contador Suspend\/Resume para el nivel de generación de perfiles especificado.  
  
## Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
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
 El valor inicial del contador Suspend\/Resume es 0.  Cada llamada a SuspendProfile suma 1 a este contador, cada llamada a ResumeProfile le resta 1.  
  
 Cuando el valor del contador Suspend\/Resume es mayor que 0, el estado de Suspend\/Resume del nivel es OFF.  Cuando el recuento es menor o igual que 0, el estado de Suspend\/Resume es ON.  
  
 Cuando los estados de Start\/Stop y de Suspend\/Resume son ON, el estado de generación de perfiles del nivel es ON.  Para que se generen los perfiles de un subproceso los estados del subproceso en los niveles global, de proceso y de subproceso deben ser ON.  
  
## Equivalente en .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Información de la función  
 Encabezado: Declarado en VSPerf.h  
  
 Biblioteca de importación: VSPerf.lib  
  
## Ejemplo  
 En el siguiente ejemplo se ilustra el método SuspendProfile.  En este ejemplo se asume que previamente se ha realizado una llamada a StartProfile para el proceso o subproceso identificado por [PROFILE\_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)