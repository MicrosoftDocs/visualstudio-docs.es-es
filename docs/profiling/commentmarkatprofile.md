---
title: "CommentMarkAtProfile | Microsoft Docs"
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
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método `CommentMarkAtProfile` inserta un valor de marca de tiempo, una marca numérica y una cadena de comentario en el archivo .vsp.  El valor de la marca de tiempo se puede utilizar para sincronizar los eventos externos.  Para que se inserten la marca y el comentario, la generación de perfiles del subproceso que contiene la función CommentMarkAtProfile debe estar establecida en ON.  
  
## Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Parámetros  
 `dnTimestamp`  
  
 Entero de 64 bits que representa un valor de marca de tiempo.  
  
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
 El estado de generación de perfiles del subproceso que contiene la función de perfil de marcas debe estar activado cuando se inserten marcas o comentarios con el comando Mark o con las funciones de la API \(CommentMarkAtProfile, CommentMarkProfile o MarkProfile\).  Las marcas de perfil tienen un ámbito global.  Por ejemplo, una marca de perfil insertada en un subproceso se puede utilizar para marcar el inicio y el final de un segmento de datos en cualquier subproceso del archivo .vsp.  
  
> [!IMPORTANT]
>  Los métodos CommentMarkAtProfile sólo se deben utilizar con la instrumentación.  
  
## Equivalente en .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Información de la función  
  
|||  
|-|-|  
|**Encabezado**|Incluir VSPerf.h|  
|**Biblioteca**|Utilizar VSPerf.lib|  
|**Unicode**|Se implementa como CommentMarkAtProfileW \(Unicode\) y CommentMarkAtProfileA \(ANSI\).|  
  
## Ejemplo  
 El código siguiente ilustra el uso de la llamada a la función genérica CommentMarkAtProfile.  En el ejemplo se asume que se utilizan macros de cadenas de Win32 y la configuración del compilador de ANSI para determinar si el código llama a la función habilitada para ANSI.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio \(Nativa\)](../profiling/visual-studio-profiler-api-reference-native.md)