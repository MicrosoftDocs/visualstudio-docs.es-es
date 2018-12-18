---
title: 'Cómo: depurar código insertado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8efcc5780b27967644330e55dc540333a19105a2
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389343"
---
# <a name="how-to-debug-injected-code"></a>Cómo: Depurar código insertado

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Restablecer configuración](../ide/environment-settings.md#reset-settings).

El uso de atributos puede simplificar enormemente la programación en C++. Para obtener más información, consulte [conceptos](/cpp/windows/attributed-programming-concepts). El compilador se encarga de interpretar directamente algunos atributos. Otros atributos insertan código en el archivo de código fuente del programa, que el compilador se encarga entonces de compilar. Este código insertado facilita la programación al reducir la cantidad de código que se debe escribir. Sin embargo, a veces un error puede hacer que la aplicación no funcione correctamente mientras se ejecuta el código insertado. En estos casos, debería examinarse el código insertado. Visual Studio proporciona dos modos de examinar el código insertado.

- Puede ver el código insertado en la ventana **Desensamblado**.

- Mediante [/Fx](/cpp/build/reference/fx-merge-injected-code), se puede crear un archivo de código fuente combinado que contiene código original e insertado.

La ventana **Desensamblado** muestra instrucciones en lenguaje de ensamblado que corresponden al código fuente y al código insertado por los atributos. Además, la ventana **Desensamblado** puede mostrar la anotación del código fuente.

## <a name="to-turn-on-source-annotation"></a>Para activar la anotación del código fuente

-   Haga clic con el botón derecho en la ventana **Desensamblado** y elija **Mostrar código fuente** en el menú contextual.

     Si conoce la ubicación de un atributo en una ventana de código fuente, puede utilizar el menú contextual para buscar el código insertado en la ventana **Desensamblado**.

## <a name="to-view-injected-code"></a>Para ver el código insertado

1.  El depurador debe hallarse en modo de interrupción.

2.  En una ventana de código fuente, coloque el cursor delante de los atributos cuyo código insertado desea ver.

3.  Haga clic con el botón derecho y seleccione **Ir al desensamblado** en el menú contextual.

     Si la ubicación del atributo está cerca del punto de ejecución actual, puede seleccionar la ventana **Desensamblado** en el menú **Depurar**.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Para ver el código de desensamblado en el punto de ejecución actual

1.  El depurador debe hallarse en modo de interrupción.

2.  En el menú **Depurar**, elija **Ventanas** y después haga clic en **Desensamblado**.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)