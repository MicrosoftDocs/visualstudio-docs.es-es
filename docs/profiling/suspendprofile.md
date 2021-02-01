---
title: SuspendProfile | Microsoft Docs
description: Obtenga más información sobre cómo el método SuspendProfile incrementa el contador de suspensiones y reanudaciones para el nivel de generación de perfiles especificado.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 728aa7c858f8321e3289f2d17e612284f8739f17
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719271"
---
# <a name="suspendprofile"></a>SuspendProfile
El método `SuspendProfile` incrementa el contador de suspensiones y reanudaciones para el nivel de generación de perfiles especificado.

## <a name="syntax"></a>Sintaxis

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parámetros
 `Level`

 Indica el nivel de perfil en el que se puede aplicar la recopilación de datos de rendimiento. Los enumeradores **PROFILE_CONTROL_LEVEL** siguientes se pueden usar para indicar uno de tres niveles en los que se puede aplicar la recopilación de datos de rendimiento:

|Enumerador|Descripción|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|La configuración de nivel global afecta a todos los procesos y subprocesos en la generación de perfiles.|
|PROFILE_PROCESSLEVEL|La configuración de nivel de proceso afecta a todos los subprocesos que forman parte del proceso especificado.|
|PROFILE_THREADLEVEL|La configuración de nivel de generación de perfiles de subproceso afecta al subproceso especificado.|

 `dwId`

 Identificador del proceso o subproceso que genera el sistema.

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE_COMMAND_STATUS**. El valor devuelto puede ser cualquiera de los siguientes:

|Enumerador|Descripción|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|El id. del elemento de generación de perfiles no existe.|
|PROFILE_ERROR_LEVEL_NOEXIST|El nivel de generación de perfiles especificado no existe.|
|PROFILE_ERROR_MODE_NEVER|El modo de generación de perfiles se estableció en NEVER cuando se llamó a la función.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Todavía no se ha implementado la llamada a la función de generación de perfiles, el nivel de generación de perfiles o la combinación de llamada y nivel.|
|PROFILE_OK|La llamada se realizó correctamente.|

## <a name="remarks"></a>Observaciones
 El valor inicial del contador de suspensiones y reanudaciones es 0. Cada llamada a SuspendProfile suma 1 al recuento de suspensiones y reanudaciones; cada llamada a ResumeProfile resta 1.

 Cuando el recuento de suspensiones y reanudaciones es mayor que 0, el estado de suspensión y reanudación para el nivel es OFF. Cuando el recuento es menor o igual que 0, el estado de suspensión y reanudación es ON.

 Cuando el estado de Iniciar/Detener y de Suspensión/Reanudación es Activado, el estado de generación de perfiles para el nivel es Activado. Para que se pueda generar el perfil de un subproceso, los estados de nivel global, de proceso y de subproceso para el subproceso deben ser todos ON.

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Información de la función
 Encabezado: declarado en *VSPerf.h*

 Biblioteca de importación: *VSPerf.lib*

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el método SuspendProfile. En este ejemplo se da por supuesto que se ha realizado una llamada anterior a StartProfile para el proceso o subproceso identificado por [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
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

## <a name="see-also"></a>Vea también
- [Referencia de la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)
