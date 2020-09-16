---
title: Volver a la función que llamó a MFC cuando está detenido | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b05e703958fe7a1c630b542522f1f33b0fe5981
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600280"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedimiento Volver a la función que llamó a MFC cuando está detenido

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

Si ha utilizado el comando **Interrumpir** del menú **Depurar** para detener el programa y ha terminado en MFC, y está seguro de que el problema se encuentra en el código, puede usar la ventana Pila de llamadas para volver a la función. Para obtener más información, vea [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

A veces el código puede interrumpir el bombeo de mensajes. En ese caso, no hay ningún código de usuario en la pila de llamadas. Para evitar este problema, puede utilizar puntos de interrupción (posiblemente con condiciones y números de llamadas) en lugar del comando **Interrumpir**. Para obtener más información, consulta [Breakpoints and Tracepoints](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Navegación a la función desde la que se llamó a MFC

- Use la ventana **Pila de llamadas**.

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)