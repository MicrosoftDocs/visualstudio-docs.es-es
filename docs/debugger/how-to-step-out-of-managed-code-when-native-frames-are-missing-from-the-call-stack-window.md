---
title: Fuera del C# cuando faltan marcos nativos en la pila de llamadas de código | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25021f0c3daffdaf59633fdb9bff0e2659f43d2e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043030"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procedimiento Salida del código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas

Si el código tiene marcos nativos que no se ven en la ventana **Pila de llamadas**, salir de código administrado puede generar resultados inesperados. Como solución, puede utilizar un punto de interrupción en lugar de **Paso a paso para salir**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Salga de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas

1.  En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.

2.  En el menú **Depurar**, elija **Continuar**.

     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.

## <a name="see-also"></a>Vea también

- [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)