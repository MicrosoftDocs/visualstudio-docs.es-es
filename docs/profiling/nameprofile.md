---
title: "NameProfile | Microsoft Docs"
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
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La función `NameProfile` asigna una cadena al proceso o subproceso especificado.  
  
 La API de NameProfile sólo está disponible para la generación de perfiles de instrumentación.  La API NameProfile no se admite para la generación de perfiles de muestreo.  
  
## Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Parámetros  
 `pszName`  
  
 Nombre del elemento de generación de perfiles.  Un nombre no es válido \(lo que hace que NameProfileA devuelva NAME\_ERROR\_INVALID\_NAME\) si:  
  
-   El puntero que se ha pasado en NameProfileA es un valor NULL  
  
-   Los datos de cadena de pszName comienzan con un número  
  
-   Los datos de cadena de pszName contienen un espacio  
  
-   Los datos de cadena de pszName contiene cualquiera de los siguientes caracteres: ;. ¡\`~\! @\#$%^\*&\(\) \= \[\] {}&#124;¿\\? \/\<\>  
  
 `Level`  
  
 Indica el nivel de perfil al que se puede aplicar la recolección de datos de rendimiento.  Los valores **PROFILE\_CONTROL\_LEVEL** siguientes se pueden utilizar para indicar uno de los tres niveles a los que se puede aplicar la recolección de datos de rendimiento:  
  
|Enumerator|Descripción|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|La configuración de nivel global afecta a todos los procesos y subprocesos de la ejecución de generación de perfiles.|  
|PROFILE\_PROCESSLEVEL|La configuración de nivel de proceso afecta a todos los subprocesos que forman parte del proceso especificado.|  
|PROFILE\_THREADLEVEL|La configuración de nivel de subprocesos de la generación de perfiles afecta al subproceso especificado.|  
  
 `dwId`  
  
 Identificador del nivel de generación de perfiles.  Se debe utilizar el identificador del proceso o del subproceso generado por el sistema.  
  
## Valor de propiedad y valor devuelto  
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE\_COMMAND\_STATUS**.  El valor devuelto puede ser cualquiera de los siguientes:  
  
|Enumerator|Descripción|  
|----------------|-----------------|  
|NAME\_ERROR\_ID\_NOEXIST|El elemento de generación de perfiles especificado no existe.|  
|NAME\_ERROR\_INVALID\_NAME|El nombre no es válido.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|El nivel de perfil especificado no existe.|  
|NAME\_ERROR\_NO\_SUPPORT|No se admite la operación especificada.|  
|NAME\_ERROR\_OUTOFMEMORY|La memoria no estaba disponible para registrar el evento.|  
|NAME\_ERROR\_REDEFINITION|Ya se asignó un nombre al elemento de perfil.  Se omite el nombre que figura en esta función.|  
|NAME\_ERROR\_TEXTTRUNCATED|El texto del nombre superó 32 caracteres incluido el carácter null y, por consiguiente, se truncó.|  
|NAME\_OK|El nombre se registró correctamente.|  
  
## Comentarios  
 Sólo se puede asignar un nombre a cada proceso o subproceso.  Una vez asignado el nombre a un elemento de generación de perfiles, se omiten las llamadas subsiguientes a NameProfile para ese elemento.  
  
 Si se asigna el mismo nombre a subprocesos o procesos diferentes, el informe incluirá los datos de todos los elementos del nivel que tengan ese nombre.  
  
 Si especifica un proceso o subproceso distinto del actual, debe asegurarse de que se ha inicializado y que ha comenzado a ejecutarse antes de asignarle el nombre.  De lo contrario, se producirá un error en el método NameProfile.  
  
> [!IMPORTANT]
>  Las funciones API CreateProcess\(\) y CreateThread\(\) pueden devolver valores antes de que se inicialice el subproceso o proceso.  
  
## Equivalente en .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Información de la función  
  
|||  
|-|-|  
|**Encabezado**|Incluir VSPerf.h|  
|**Biblioteca**|Utilizar VSPerf.lib|  
|**Unicode**|Se implementa como `NameProfileW` \(Unicode\) y `NameProfileA` \(ANSI\).|  
  
## Ejemplo  
 El código siguiente muestra la llamada a la función NameProfile.  En el ejemplo se asume que se utilizan macros de cadenas de Win32 y la configuración del compilador de ANSI para determinar si el código llama a la función habilitada para ANSI.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)