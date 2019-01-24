---
title: Volver a la función que llamó a MFC cuando está detenido | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9b3d95108ac91066da51feed9f5813d15693d52
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988344"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedimiento Volver a la función que llamó a MFC cuando está detenido

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

Si ha utilizado el comando **Interrumpir** del menú **Depurar** para detener el programa y ha terminado en MFC, y está seguro de que el problema se encuentra en el código, puede usar la ventana Pila de llamadas para volver a la función. Para obtener más información, vea [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

A veces el código puede interrumpir el bombeo de mensajes. En ese caso, no hay ningún código de usuario en la pila de llamadas. Para evitar este problema, puede utilizar puntos de interrupción (posiblemente con condiciones y números de llamadas) en lugar del comando **Interrumpir**. Para obtener más información, consulta [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Vaya a la función desde el que se llamó a MFC

-   Use la ventana **Pila de llamadas**.

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)