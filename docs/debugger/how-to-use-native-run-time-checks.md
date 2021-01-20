---
title: Uso de comprobaciones nativas en tiempo de ejecución | Microsoft Docs
description: Use comprobaciones nativas en tiempo de ejecución en Visual Studio para detectar errores en tiempo de ejecución comunes, como daños en el puntero de pila, saturaciones de matrices locales y daños en la pila.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 70f047fa84513821812a13f7dee3136d2d431d9a
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240249"
---
# <a name="how-to-use-native-run-time-checks"></a>Procedimiento Uso de comprobaciones nativas en tiempo de ejecución
En un proyecto de C++ de Visual Studio, puede realizar [runtime_checks](/cpp/preprocessor/runtime-checks) de forma nativa para detectar errores en tiempo de ejecución, tales como:

- Daños en el puntero de la pila

- Saturación de matrices locales

- Daños en la pila

- Dependencias en variables locales sin inicializar

- Pérdida de datos en una asignación a una variable corta.

  Si utiliza **/RTC** con una generación optimizada ( **/O**), obtendrá un error del compilador. Si utiliza un pragma `runtime_checks` en una versión optimizada, el pragma no surte ningún efecto.

  Cuando se depura un programa con las comprobaciones en tiempo de ejecución habilitadas, la acción predeterminada es la de que el programa se detenga y se interrumpa su depuración cuando se produzca un error en tiempo de ejecución. Puede cambiar este comportamiento predeterminado para cualquier comprobación en tiempo de ejecución. Para obtener más información, vea [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).

  Los siguientes procedimientos describen cómo habilitar las comprobaciones en tiempo de ejecución nativas en una versión de depuración y cómo modificar el comportamiento de la comprobación en tiempo de ejecución nativa.

  Los demás temas de esta sección contienen información sobre:

- [Personalizar las comprobaciones en tiempo de ejecución con la biblioteca en tiempo de ejecución de C](../debugger/native-run-time-checks-customization.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Para habilitar las comprobaciones nativas en tiempo de ejecución en una versión de depuración

- Utilice la opción **/RTC** y vincule la versión de depuración de una biblioteca C en tiempo de ejecución (/MDd, por ejemplo).

### <a name="to-modify-native-run-time-check-behavior"></a>Para modificar el comportamiento de las comprobaciones nativas en tiempo de ejecución

- Utilice la directiva pragma `runtime_checks` .

## <a name="see-also"></a>Vea también
- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Comprobar errores en tiempo de ejecución](/cpp/c-runtime-library/run-time-error-checking)