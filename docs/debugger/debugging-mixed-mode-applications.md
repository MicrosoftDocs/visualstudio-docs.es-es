---
title: Depuración de aplicaciones en modo mixto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4170a63597611bb190a6b3cf365b6dbced1bc9ae
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389395"
---
# <a name="debugging-mixed-mode-applications"></a>Depurar aplicaciones en modo mixto
Una aplicación en modo mixto es cualquier aplicación que combine código nativo (C++) y código administrado (como Visual Basic, Visual C# o C++ administrado que se ejecute en Common Language Runtime). La depuración de aplicaciones en modo mixto es un proceso en gran medida transparente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; no difiere mucho de la depuración de una aplicación en modo individual. Sin embargo, existen consideraciones especiales.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Habilitar Editar y continuar de C++ en la depuración en modo mixto

Para habilitar editar y continuar para C++, vea [cómo habilitar y deshabilitar Editar y continuar](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Para usar Editar y Continuar para C++ en Visual Studio 2013, tiene que revertir al motor de depuración heredado. Vea [Switching to Managed Compatibility Mode in Visual Studio 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/) (Cambiar al modo de compatibilidad administrado en Visual Studio 2013) en el blog Microsoft Application Lifecycle Management.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Evaluación de propiedades en aplicaciones en modo mixto
 En las aplicaciones en modo mixto, la evaluación de propiedades por parte del depurador es una operación costosa. En consecuencia, las operaciones de depuración como la ejecución paso a paso pueden parecer lentas. Para obtener más información, vea [Code Stepping Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) (Información general sobre cómo ejecutar código). Si se produce un rendimiento muy bajo en la depuración en modo mixto, puede desactivar la evaluación de propiedades en las ventanas del depurador.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Restablecer configuración](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Para desactivar la evaluación de propiedades

1. En el menú **Herramientas** , elija **Opciones**.

2. En el cuadro de diálogo **Opciones**, abra la carpeta **Depuración** y seleccione la categoría **General**.

3. Desactive la casilla **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.

   Puesto que las pilas de llamadas nativas y las administradas son diferentes, el depurador no siempre proporciona la pila de llamadas competa para el código mixto. Cuando el código nativo llama a código administrado, quizá observe algunas discrepancias. Para obtener más información, vea [Mixed Code and Missing Information in the Call Stack Window](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md) (Código mixto e información no mostrada en la ventana Pila de llamadas).

## <a name="see-also"></a>Vea también

- [Depurar código administrado](../debugger/debugging-managed-code.md)