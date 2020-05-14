---
title: Procedimiento Depuración en modo mixto | Microsoft Docs
ms.date: 11/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f58c51bf1b610375c6204e27d064870ce1f76d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894383"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Procedimiento Depuración en modo mixto (C#, C++ y Visual Basic)

En los procedimientos siguientes se describe cómo habilitar la depuración del código administrado y nativo, también conocida como depuración en modo mixto. Hay dos escenarios de depuración en modo mixto:

- La aplicación que llama a un archivo DLL está escrita en código nativo y el archivo DLL, en código administrado.

- La aplicación que llama a un archivo DLL está escrita en código administrado y el archivo DLL, en código nativo. Para consultar un tutorial más detallado sobre este escenario, vea [Tutorial: Depuración de C# y C++ en la misma sesión de depuración](../debugger/how-to-debug-managed-and-native-code.md).

Puede habilitar los depuradores administrados y nativos en las páginas **Propiedad** del proyecto de la aplicación que realiza la llamada. La configuración difiere entre aplicaciones nativas y administradas.

Si no tiene acceso al proyecto de la aplicación que realiza la llamada, puede depurar el archivo DLL desde el proyecto DLL. No es necesario el modo mixto para depurar solo el proyecto DLL. Para obtener más información, vea [Cómo: Depuración desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Es posible que los cuadros de diálogo y los comandos que se muestren difieran de los que se incluyen en este artículo, en función de los valores de configuración o de la edición de Visual Studio. Para cambiar la configuración, seleccione **Herramientas** > **Importar y exportar configuraciones**. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Habilitación de la depuración en modo mixto para una aplicación de llamadas nativa

1. Seleccione el proyecto de C++ en **Explorador de soluciones**, haga clic en el icono **Propiedades** y presione **Alt**+**Entrar**, o haga clic con el botón derecho y seleccione **Propiedades**.

1. En el cuadro de diálogo **\<Proyecto > Páginas de propiedades**, expanda el nodo **Propiedades de configuración** y, a continuación, seleccione **Depuración**.

1. Establezca el **Tipo de depurador** en **Mixto** o **Automático**.

1. Seleccione **Aceptar**.

   ![Habilitación de la depuración en modo mixto](../debugger/media/dbg-mixed-mode-from-native.png "Habilitación de la depuración en modo mixto")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Habilitación de la depuración en modo mixto para una aplicación de llamadas administrada

1. Seleccione el proyecto de C# o Visual Basic en **Explorador de soluciones**, seleccione el icono **Propiedades** y presione **Alt**+**Entrar**, o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Depurar** y, a continuación, seleccione **Habilitar depuración de código nativo**.

1. Cierre la página de propiedades para guardar los cambios.

   ![Habilitación de la depuración de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Habilitación de la depuración de código nativo")

> [!NOTE]
> En la mayoría de las versiones de Visual Studio a partir de Visual Studio 2017, debe usar el archivo *launchSettings.json* en lugar de las propiedades del proyecto para habilitar la depuración en modo mixto para el código nativo de una aplicación .NET Core. Para obtener más información, consulte [Tutorial: Depuración de C# y C++ en la misma sesión de depuración](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vea también

- [Cómo: Depuración desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)