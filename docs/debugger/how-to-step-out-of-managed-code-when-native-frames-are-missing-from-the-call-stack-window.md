---
title: 'Cómo: salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5c671f93e20da108a9fd1069a0950f52ef00da9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388574"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Cómo: Salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas

Si el código tiene marcos nativos que no se ven en la ventana Pila de llamadas **, salir de código administrado puede generar resultados inesperados. Como solución, puede utilizar un punto de interrupción en lugar de Paso a paso para salir **.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Restablecer configuración](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para salir de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas

1.  En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.

2.  En el menú Depurar **, elija Continuar**.

     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.

## <a name="see-also"></a>Vea también

- [Cómo: Usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)