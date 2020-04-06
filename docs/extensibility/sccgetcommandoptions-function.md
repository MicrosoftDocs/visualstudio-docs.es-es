---
title: Función SccGetCommandOptions ( SccGetCommandOptions) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700836"
---
# <a name="sccgetcommandoptions-function"></a>Función SccGetCommandOptions
Esta función solicita al usuario opciones avanzadas para un comando determinado.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 Icommand

[en] El comando para el que se solicitan opciones avanzadas (consulte [Código de comando](../extensibility/command-code-enumerator.md) para ver los valores posibles).

 ppvOptions

[en] La estructura de opciones `NULL`(también puede ser ).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_I_ADV_SUPPORT|El complemento de control de código fuente admite opciones avanzadas para el comando.|
|SCC_I_OPERATIONCANCELED|El usuario canceló el cuadro de diálogo **Opciones** del complemento de control de código fuente.|
|SCC_E_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|
|SCC_E_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está actualmente desprotegido.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta `ppvOptions` = `NULL` función por primera vez con para determinar si el complemento de control de código fuente admite la característica de opciones avanzadas para el comando especificado. Si el complemento admite la característica para ese comando, el IDE llama a esta función de nuevo cuando el usuario solicita opciones avanzadas `ppvOptions` (normalmente `NULL` implementadas como un botón **Avanzado** en un cuadro de diálogo) y proporciona un puntero no NULL para que apunte a un puntero. El complemento almacena las opciones avanzadas especificadas por el usuario en una `ppvOptions`estructura privada y devuelve un puntero a esa estructura en . A continuación, esta estructura se pasa a todas las demás funciones de `SccGetCommandOptions` la API de complemento de Control de código fuente que necesitan conocerla, incluidas las llamadas posteriores a la función.

 Un ejemplo puede ayudar a aclarar esta situación.

 Un usuario elige el **Get** comando y el IDE muestra un **Obtener** cuadro de diálogo. El IDE `SccGetCommandOptions` llama `iCommand` a `SCC_COMMAND_GET` la `ppvOptions` función con establecido en y establecido en `NULL`. Esto es interpretado por el complemento de control de código fuente como la pregunta, "¿Tiene alguna opción avanzada para este comando?" Si el complemento `SCC_I_ADV_SUPPORT`devuelve , el IDE muestra un botón **Avanzado** en el cuadro de diálogo **Obtener.**

 La primera vez`NULL``ppvOptions` que el usuario hace clic en `SccGetCommandOptions` **el** avanzado botón, el IDE vuelve a llamar a la función, esta vez con un no que apunta a un `NULL` puntero. El complemento muestra su propio cuadro de diálogo **Obtener opciones,** solicita al usuario información, coloca esa información `ppvOptions`en su propia estructura y devuelve un puntero a esa estructura en .

 Si el usuario vuelve a hacer clic en **Avanzado** `SccGetCommandOptions` en el `ppvOptions`mismo cuadro de diálogo, el IDE vuelve a llamar a la función sin cambiar, para que la estructura se devuelva al complemento. Esto permite que el complemento reinicialice su cuadro de diálogo en los valores que el usuario había establecido previamente. El complemento modifica la estructura en su lugar antes de volver.

 Por último, cuando el usuario hace clic en **Aceptar** en el Cuadro de diálogo **Obtener** del `ppvOptions` IDE, el IDE llama a [SccGet](../extensibility/sccget-function.md), pasando la estructura devuelta que contiene las opciones avanzadas.

> [!NOTE]
> El `SCC_COMMAND_OPTIONS` comando se utiliza cuando el IDE muestra un cuadro de diálogo **Opciones** que permite al usuario establecer preferencias que controlan cómo funciona la integración. Si el complemento de control de código fuente desea proporcionar su propio cuadro de diálogo de preferencias, puede mostrarlo desde un botón **Avanzado** en el cuadro de diálogo de preferencias del IDE. El plug-in es el único responsable de obtener y conservar esta información; el IDE no lo usa ni lo modifica.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
