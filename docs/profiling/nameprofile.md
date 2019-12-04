---
title: NameProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9f0c9a3259186e1581a4673cdc18d1554e92b3c
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778497"
---
# <a name="nameprofile"></a>NameProfile
La función `NameProfile` asigna una cadena al subproceso o el proceso especificado.

 La API NameProfile solamente está disponible para la generación de perfiles de instrumentación. La API NameProfile no se admite para la generación de perfiles de muestreo.

## <a name="syntax"></a>Sintaxis

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parámetros
 `pszName`

 El nombre del elemento de generación de perfiles. Un nombre no es válido (como consecuencia, NameProfileA devuelve NAME_ERROR_INVALID_NAME) si:

- El puntero pasado en NameProfileA es un valor NULL.

- Los datos de cadena de pszName empiezan con un número.

- Los datos de cadena de pszName empiezan con un espacio.

- Los datos de cadena de pszName contienen cualquiera de los siguientes caracteres: ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>

  `Level`

  Indica el nivel de perfil en el que se puede aplicar la recopilación de datos de rendimiento. Los valores **PROFILE_CONTROL_LEVEL** siguientes se pueden usar para indicar uno de tres niveles en los que se puede aplicar la recopilación de datos de rendimiento:

|Enumerador|DESCRIPCIÓN|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|La configuración de nivel global afecta a todos los procesos y subprocesos en la generación de perfiles.|
|PROFILE_PROCESSLEVEL|La configuración de nivel de proceso afecta a todos los subprocesos que forman parte del proceso especificado.|
|PROFILE_THREADLEVEL|La configuración de nivel de generación de perfiles de subproceso afecta al subproceso especificado.|

 `dwId`

 Identificador del nivel de generación de perfiles. Usa el identificador del proceso o subproceso generado por el sistema.

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto
 La función indica si la operación es correcta o errónea mediante la enumeración **PROFILE_COMMAND_STATUS**. El valor devuelto puede ser cualquiera de los siguientes:

|Enumerador|DESCRIPCIÓN|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|El elemento de generación de perfiles especificado no existe.|
|NAME_ERROR_INVALID_NAME|El nombre no es válido.|
|NAME_ERROR_LEVEL_NOEXIST|El nivel del perfil especificado no existe.|
|NAME_ERROR_NO_SUPPORT|La operación especificada no se admite.|
|NAME_ERROR_OUTOFMEMORY|La memoria no estaba disponible para registrar el evento.|
|NAME_ERROR_REDEFINITION|Ya se asignó un nombre para el elemento de perfil. Se omite el nombre de esta función.|
|NAME_ERROR_TEXTTRUNCATED|El texto del nombre supera los 32 caracteres incluido el carácter nulo y, por tanto, se truncó.|
|NAME_OK|El nombre se registró correctamente.|

## <a name="remarks"></a>Comentarios
 Solo se puede asignar un nombre a cada proceso o subproceso. Después de asignar un nombre a un elemento de generación de perfiles, se omiten las llamadas subsiguientes a NameProfile para ese elemento.

 Si se especifica el mismo nombre para diferentes subprocesos o procesos, el informe incluirá datos de todos los elementos en ese nivel con ese nombre.

 Si especifica un proceso o subproceso distinto del actual, debe asegurarse de que se ha inicializado y empezó a ejecutarse antes de asignarle el nombre. En caso contrario, se produce un error en el método NameProfile.

> [!IMPORTANT]
> Las funciones CreateProcess() y CreateThread() de la API pueden devolver un valor antes de que se inicialice el subproceso o el proceso.

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Información de la función

|||
|-|-|
|**Header**|Incluir *VSPerf.h*|
|**Library**|Usar *VSPerf.lib*|
|**Unicode**|Implementado como `NameProfileW` (Unicode) y `NameProfileA` (ANSI).|

## <a name="example"></a>Ejemplo
 El código siguiente ilustra la llamada a la función NameProfile. En el ejemplo se da por supuesto que se usan macros de cadenas de Win32 y la configuración del compilador para ANSI con el fin de determinar si el código llama a la función habilitada para ANSI.

```cpp
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

## <a name="see-also"></a>Vea también
- [Referencia de la API del generador de perfiles de Visual Studio (nativa)](../profiling/visual-studio-profiler-api-reference-native.md)
