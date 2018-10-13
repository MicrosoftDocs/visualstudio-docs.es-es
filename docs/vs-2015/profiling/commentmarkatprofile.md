---
title: CommentMarkAtProfile | Microsoft Docs
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
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9a3f1c33deb1cae18b43d43af6ded9a8ea2c8ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268442"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El método `CommentMarkAtProfile` inserta un valor de marca de tiempo, una marca numérica y una cadena de comentario en el archivo .vsp. El valor de marca de tiempo se puede usar para sincronizar eventos externos. Para que la marca y el comentario se inserten, la generación de perfiles para el subproceso que contiene la función CommentMarkAtProfile debe estar activada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dnTimestamp`  
  
 Entero de 64 bits que representa un valor de marca de tiempo.  
  
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
 El estado de generación de perfiles del subproceso que contiene la función de perfil de marcas debe estar activado cuando se inserten marcas o comentarios con el comando Mark o con las funciones de la API (CommentMarkAtProfile, CommentMarkProfile o MarkProfile). Las marcas de perfil tienen un ámbito global. Por ejemplo, una marca de perfil insertada en un subproceso se puede utilizar para marcar el inicio y el final de un segmento de datos en cualquier subproceso del archivo .vsp.  
  
> [!IMPORTANT]
>  Los métodos CommentMarkAtProfile solo se deben usar con instrumentación.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Información de la función  
  
|||  
|-|-|  
|**Header**|Incluye VSPerf.h|  
|**Library**|Usa VSPerf.lib|  
|**Unicode**|Se implementa como CommentMarkAtProfileW (Unicode) y CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra el uso de la llamada de función genérica CommentMarkAtProfile. En el ejemplo se da por supuesto que se usan macros de cadenas de Win32 y la configuración del compilador para ANSI con el fin de determinar si el código llama a la función habilitada para ANSI.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)



