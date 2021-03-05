---
description: Esta función solicita al usuario opciones avanzadas para un comando determinado.
title: Función SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 400b778cf5e26b0cabad0fb19c548b2faa0a803f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220812"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions función)
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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 iCommand

de Comando para el que se solicitan opciones avanzadas (vea el [código de comando](../extensibility/command-code-enumerator.md) para ver los posibles valores).

 ppvOptions

de La estructura de la opción (también puede ser `NULL` ).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_I_ADV_SUPPORT|El complemento de control de código fuente admite opciones avanzadas para el comando.|
|SCC_I_OPERATIONCANCELED|El usuario canceló el cuadro de diálogo **Opciones** del complemento de control de código fuente.|
|SCC_E_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|
|SCC_E_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está desprotegido actualmente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función por primera vez con `ppvOptions` = `NULL` para determinar si el complemento de control de código fuente admite la característica opciones avanzadas del comando especificado. Si el complemento admite la característica para ese comando, el IDE llama de nuevo a esta función cuando el usuario solicita opciones avanzadas (normalmente se implementa como un botón **avanzado** en un cuadro de diálogo) y proporciona un puntero no nulo para `ppvOptions` que señala a un `NULL` puntero. El complemento almacena las opciones avanzadas especificadas por el usuario en una estructura privada y devuelve un puntero a esa estructura en `ppvOptions` . A continuación, esta estructura se pasa a todas las demás funciones de la API del complemento de control de código fuente que necesiten conocer información, incluidas las llamadas subsiguientes a la `SccGetCommandOptions` función.

 Un ejemplo puede ayudar a aclarar esta situación.

 Un usuario elige el comando **Get** y el IDE muestra un cuadro de diálogo **obtener** . El IDE llama a la `SccGetCommandOptions` función con `iCommand` establecido en `SCC_COMMAND_GET` y `ppvOptions` establecido en `NULL` . El complemento de control de código fuente interpreta esto como la pregunta "¿tiene opciones avanzadas para este comando?". Si el complemento devuelve `SCC_I_ADV_SUPPORT` , el IDE muestra un botón **avanzado** en el cuadro de diálogo **obtener** .

 La primera vez que el usuario hace clic en el botón **avanzadas** , el IDE llama de nuevo a la `SccGetCommandOptions` función, esta vez con un `NULL``ppvOptions` que no señala a un `NULL` puntero. El complemento muestra su propio cuadro de diálogo **obtener opciones** , solicita información al usuario, coloca esa información en su propia estructura y devuelve un puntero a esa estructura en `ppvOptions` .

 Si el usuario vuelve a hacer clic en **Opciones avanzadas** en el mismo cuadro de diálogo, el IDE llama de nuevo a la `SccGetCommandOptions` función sin cambiar `ppvOptions` , de modo que la estructura se pasa de nuevo al complemento. Esto permite que el complemento reinicialice su cuadro de diálogo con los valores que el usuario había establecido previamente. El complemento modifica la estructura en su lugar antes de volver.

 Por último, cuando el usuario hace clic en **Aceptar** en el cuadro de diálogo **obtener** del IDE, el IDE llama a [SccGet](../extensibility/sccget-function.md), pasando la estructura devuelta en `ppvOptions` que contiene las opciones avanzadas.

> [!NOTE]
> El comando `SCC_COMMAND_OPTIONS` se usa cuando el IDE muestra un cuadro de diálogo de **Opciones** que permite al usuario establecer las preferencias que controlan el funcionamiento de la integración. Si el complemento de control de código fuente desea proporcionar su propio cuadro de diálogo Preferencias, puede mostrarlo desde un botón **avanzado** del cuadro de diálogo Preferencias del IDE. El complemento es el único responsable de obtener y conservar esta información; el IDE no lo utiliza ni lo modifica.

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
