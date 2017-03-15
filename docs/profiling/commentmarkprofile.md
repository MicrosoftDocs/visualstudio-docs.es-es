---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La función `CommentMarkProfile` inserta un marcador numérico y una cadena de texto en el archivo .vsp.  Para que se inserten la marca y el comentario, la generación de perfiles del subproceso que contiene la función `CommentMarkProfile` debe estar establecida en ON.  
  
## Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### Parámetros  
 `lMarker`  
  
 Marcador numérico que se inserta.  El marcador debe ser mayor o igual que 0 \(cero\).  
  
 `szComment`  
  
 Puntero a la cadena de texto que se inserta.  La cadena debe ser tener menos de 256 caracteres incluido el terminador NULL.  
  
## Valor de propiedad y valor devuelto  
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE\_COMMAND\_STATUS**.  El valor devuelto puede ser cualquiera de los siguientes:  
  
|Enumerator|Descripción|  
|----------------|-----------------|  
|MARK\_ERROR\_MARKER\_RESERVED|El parámetro es menor o igual que 0.  Estos valores están reservados.  La marca y el comentario no se registran.|  
|MARK\_ERROR\_MODE\_NEVER|El modo de generación de perfiles se estableció en NEVER cuando se llamó a la función.  La marca y el comentario no se registran.|  
|MARK\_ERROR\_MODE\_OFF|El modo de generación de perfiles se estableció en OFF cuando se llamó a la función.  La marca y el comentario no se registran.|  
|MARK\_ERROR\_NO\_SUPPORT|No se admite ninguna marca en este contexto.  La marca y el comentario no se registran.|  
|MARK\_ERROR\_OUTOFMEMORY|La memoria no estaba disponible para registrar el evento.  La marca y el comentario no se registran.|  
|MARK\_TEXTTOOLONG|La cadena supera el máximo de 256 caracteres.  La cadena del comentario se trunca y se registran la marca y el comentario.|  
|MARK\_OK|Se devuelve MARK\_OK para indicar que la operación es correcta.|  
  
## Comentarios  
 El estado de generación de perfiles del subproceso que contiene la función de perfil de marcas debe estar activado cuando se inserten marcas o comentarios con el comando VSInstr Mark o con funciones \(CommentMarkAtProfile, CommentMarkProfile o MarkProfile\).  
  
 Las marcas de perfil tienen un ámbito global.  Por ejemplo, una marca de perfil insertada en un subproceso se puede utilizar para marcar el inicio y el final de un segmento de datos en cualquier subproceso del archivo .vsp.  
  
> [!IMPORTANT]
>  El método CommentMarkProfile sólo se puede utilizar con la instrumentación.  
  
## Equivalente en .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Información de la función  
  
|||  
|-|-|  
|**Encabezado**|Incluir VSPerf.h|  
|**Biblioteca**|Utilizar VSPerf.lib|  
|**Unicode**|Se implementa como `CommentMarkProfileW` \(Unicode\) y `CommentMarkProfileA` \(ANSI\).|  
  
## Ejemplo  
 El código siguiente muestra la llamada a la función CommentMarkProfile.  En el ejemplo se da por hecho que se utilizan macros de cadenas de Win32 y la configuración del compilador Unicode para determinar si el código realiza una llamada a la función [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)