---
title: Personalización de las comprobaciones nativas en tiempo de ejecución | Microsoft Docs
description: Obtenga información sobre las formas de personalizar la comprobación en tiempo de ejecución, incluidas la especificación de un destino de mensaje, la escritura de una función de informe de errores y la consulta de información de errores.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 33c3da5387c67e14ced99918273800709b3b67b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913120"
---
# <a name="native-run-time-checks-customization"></a>Personalización de las comprobaciones nativas en tiempo de ejecución
Cuando se compila con la opción **/RTC** (comprobaciones en tiempo de ejecución) o se usa el pragma `runtime_checks`, la biblioteca en tiempo de ejecución de C proporciona comprobaciones nativas en tiempo de ejecución. En algunos casos puede ser conveniente personalizar las comprobaciones en tiempo de ejecución:

- Para enviar los mensajes de comprobación en tiempo de ejecución a un archivo o a un destino distinto del predeterminado.

- Para especificar un destino de salida para los mensajes de comprobación en tiempo de ejecución en un depurador de otro proveedor.

- Para generar mensajes de comprobación en tiempo de ejecución desde un programa compilado con una versión de distribución de la biblioteca en tiempo de ejecución de C. Las versiones de distribución de la biblioteca no utilizan `_CrtDbgReportW` para generar informes de errores en tiempo de ejecución. En su lugar, abren un cuadro de diálogo **Aserción** para cada error en tiempo de ejecución.

  Para personalizar la comprobación de errores en tiempo de ejecución, puede:

- Escriba una función que crea un informe de error en tiempo de ejecución. Para obtener más información, vea [Cómo: Escritura de una función para generar informes de errores en tiempo de ejecución](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Personalizar el destino del mensaje de error.

- Consultar información sobre los errores de comprobación en tiempo de ejecución.

## <a name="customize-the-error-message-destination"></a>Personalizar el destino de los mensajes de error
 Si utiliza `_CrtDbgReportW` para generar informes de errores, puede usar `_CrtSetReportMode` para especificar el destino de los mensajes de error.

 Si usa una función de generación de informes personalizada, utilice `_RTC_SetErrorType` para asociar un error a un tipo de informe.

## <a name="query-for-information-about-run-time-checks"></a>Consultar información acerca de las comprobaciones en tiempo de ejecución
 `_RTC_NumErrors` devuelve el número de tipos de errores detectados por las comprobaciones de errores en tiempo de ejecución. Para obtener una breve descripción de cada error, puede recorrer con un bucle desde 0 al valor devuelto `_RTC_NumErrors`, pasando el valor de la iteración a `_RTC_GetErrDesc` en cada bucle. Para más información, vea [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) y [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Vea también
- [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)