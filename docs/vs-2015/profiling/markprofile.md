---
title: MarkProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 105e81ed15a540a0c008eb94cb4af49caa099879
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803035"
---
# <a name="markprofile"></a>MarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El método `MarkProfile` inserta una marca de perfil en el archivo .vsp. La generación de perfiles para el subproceso que contiene la función `MarkProfile` debe estar activada (ON) para que se inserte la marca.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lMarker`  
  
 Marcador que se inserta. El marcador debe ser mayor o igual que 0 (cero).  
  
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
 El valor de marca se inserta en el archivo .vsp cada vez que el código se ejecuta si se generan los perfiles del subproceso que contiene la función MarkProfile. Puede llamar varias veces a MarkProfile.  
  
 Las marcas de perfil tienen un ámbito global. Por ejemplo, una marca de perfil insertada en un subproceso se puede utilizar para marcar el inicio y el final de un segmento de datos en cualquier subproceso del archivo .vsp.  
  
 El estado de generación de perfiles del subproceso que contiene la función de perfil de marcas debe estar activado cuando se inserten marcas o comentarios con el comando Mark o con las funciones de la API (CommentMarkAtProfile, CommentMarkProfile o MarkProfile).  
  
> [!IMPORTANT]
>  El método MarkProfile solo se debe utilizar con la generación de perfiles de instrumentación.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Información de la función  
 Encabezado: declarado en VSPerf.h  
  
 Biblioteca de importación: VSPerf.lib  
  
## <a name="example"></a>Ejemplo  
 El código siguiente ilustra la función MarkProfile.  
  
```  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia a la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)
