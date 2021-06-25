---
description: Esta función solicita al usuario opciones avanzadas para un comando determinado.
title: Función SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7972d874668649b8bb86adc15008880c5fc4152e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903936"
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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 Icommand

[in] Comando para el que se solicitan opciones avanzadas (vea [Código de comando](../extensibility/command-code-enumerator.md) para ver los valores posibles).

 ppvOptions

[in] La estructura de opciones (también puede ser `NULL` ).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_I_ADV_SUPPORT|El complemento de control de código fuente admite opciones avanzadas para el comando.|
|SCC_I_OPERATIONCANCELED|El usuario canceló el cuadro de diálogo Opciones del complemento de control **de** código fuente.|
|SCC_E_OPTNOTSUPPORTED|El complemento de control de código fuente no admite esta operación.|
|SCC_E_ISCHECKEDOUT|No se puede realizar esta operación en un archivo que está desprotegiendo actualmente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función por primera vez con para determinar si el complemento de control de código fuente admite la característica de opciones avanzadas `ppvOptions` = `NULL` para el comando especificado. Si el complemento admite la característica para ese comando, el IDE llama de nuevo a esta  función cuando el usuario solicita opciones avanzadas (normalmente implementadas como un botón Avanzado en un cuadro de diálogo) y proporciona un puntero que no es NULL para que apunta a un `ppvOptions` `NULL` puntero. El complemento almacena las opciones avanzadas especificadas por el usuario en una estructura privada y devuelve un puntero a esa estructura en `ppvOptions` . A continuación, esta estructura se pasa a todas las demás funciones de la API del complemento de control de código fuente que necesitan conocerla, incluidas las llamadas posteriores a la `SccGetCommandOptions` función.

 Un ejemplo puede ayudar a aclarar esta situación.

 Un usuario elige el **comando Obtener** y el IDE muestra un cuadro **de diálogo** Obtener. El IDE llama a `SccGetCommandOptions` la función con establecido en y establecido en `iCommand` `SCC_COMMAND_GET` `ppvOptions` `NULL` . El complemento de control de código fuente interpreta esto como la pregunta "¿Tiene alguna opción avanzada para este comando?". Si el complemento devuelve `SCC_I_ADV_SUPPORT` , el IDE muestra un botón **Avanzado** en su cuadro **de diálogo** Obtener.

 La primera vez que  el usuario hace clic en el botón Avanzado, el IDE vuelve a llamar a la función, esta vez con un valor que no es que apunta `SccGetCommandOptions` a un `NULL``ppvOptions` `NULL` puntero. El complemento muestra su  propio cuadro de diálogo Obtener opciones, solicita información al usuario, coloca esa información en su propia estructura y devuelve un puntero a esa estructura en `ppvOptions` .

 Si el usuario vuelve **a** hacer clic en Avanzado en el mismo cuadro de diálogo, el IDE vuelve a llamar a la función sin cambiar , de modo que la estructura se vuelva a `SccGetCommandOptions` pasar al `ppvOptions` complemento. Esto permite que el complemento reinicialice su cuadro de diálogo con los valores que el usuario había establecido previamente. El complemento modifica la estructura en su lugar antes de volver.

 Por último, cuando  el usuario hace clic en Aceptar en el cuadro de diálogo **Obtener** del IDE, el IDE llama a [SccGet](../extensibility/sccget-function.md)y pasa la estructura devuelta en que contiene las `ppvOptions` opciones avanzadas.

> [!NOTE]
> El comando se usa cuando el IDE muestra un cuadro de diálogo Opciones que permite al usuario establecer preferencias `SCC_COMMAND_OPTIONS` que controlan cómo funciona la integración.  Si el complemento de control de código fuente quiere proporcionar su  propio cuadro de diálogo de preferencias, puede mostrarlo desde un botón Avanzado del cuadro de diálogo preferencias del IDE. El complemento es el único responsable de obtener y conservar esta información. el IDE no lo usa ni lo modifica.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
