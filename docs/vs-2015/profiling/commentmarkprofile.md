---
title: CommentMarkProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d1722cd09bfb76e2ca8c72c6948923b0713100
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802946"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La función `CommentMarkProfile` inserta un marcador numérico y una cadena de texto en el archivo .vsp. Para que la marca y el comentario se inserten, la generación de perfiles para el subproceso que contiene la función `CommentMarkProfile` debe estar activada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lMarker`  
  
 Marcador numérico que se va a insertar. El marcador debe ser mayor o igual que 0 (cero).  
  
 `szComment`  
  
 Puntero a la cadena de texto que se va a insertar. La cadena debe contener menos de 256 caracteres, incluido el terminador NULL.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE_COMMAND_STATUS**. El valor devuelto puede ser cualquiera de los siguientes:  
  
|Enumerador|Descripción|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|El parámetro es menor o igual que 0. Estos valores están reservados. La marca y el comentario no se registran.|  
|MARK_ERROR_MODE_NEVER|El modo de generación de perfiles se estableció en NEVER cuando se llamó a la función. La marca y el comentario no se registran.|  
|MARK_ERROR_MODE_OFF|El modo de generación de perfiles se estableció en OFF cuando se llamó a la función. La marca y el comentario no se registran.|  
|MARK_ERROR_NO_SUPPORT|No se admite ninguna marca en este contexto. La marca y el comentario no se registran.|  
|MARK_ERROR_OUTOFMEMORY|La memoria no estaba disponible para registrar el evento. La marca y el comentario no se registran.|  
|MARK_TEXTTOOLONG|La cadena supera el máximo de 256 caracteres. La cadena del comentario se trunca y se registran la marca y el comentario.|  
|MARK_OK|Se devuelve MARK_OK para indicar que la operación es correcta.|  
  
## <a name="remarks"></a>Comentarios  
 El estado de generación de perfiles del subproceso que contiene la función de perfil de marcas debe estar activado cuando se inserten marcas o comentarios con el comando VSInstr Mark o con funciones (CommentMarkAtProfile, CommentMarkProfile o MarkProfile).  
  
 Las marcas de perfil tienen un ámbito global. Por ejemplo, una marca de perfil insertada en un subproceso se puede utilizar para marcar el inicio y el final de un segmento de datos en cualquier subproceso del archivo .vsp.  
  
> [!IMPORTANT]
>  El método CommentMarkProfile solo se puede utilizar con instrumentación.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Información de la función  
  
|||  
|-|-|  
|**Header**|Incluye VSPerf.h|  
|**Library**|Usa VSPerf.lib|  
|**Unicode**|Implementado como `CommentMarkProfileW` (Unicode) y `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Ejemplo  
 El código siguiente ilustra la llamada de función CommentMarkProfile. En el ejemplo se da por supuesto que se usan macros de cadenas de Win32 y la configuración del compilador Unicode para determinar si el código llama a la llamada de función [!INCLUDE[vcpransi](../includes/vcpransi-md.md)].  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)



