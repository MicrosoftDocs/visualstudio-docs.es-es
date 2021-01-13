---
title: Depuración en modo mixto | Microsoft Docs
description: Vea cómo habilitar la depuración en modo mixto (tanto del código administrado como del nativo) en las páginas de propiedades del proyecto de la aplicación que realiza la llamada.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: how-to
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
ms.openlocfilehash: 123fb61cb223d8db3c447f5925639df33a2b3e11
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903992"
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

1. En el cuadro de diálogo **\<Project>Páginas de propiedades**, expanda el nodo **Propiedades de configuración** y, después, seleccione **Depuración**.

1. Establezca el **Tipo de depurador** en **Mixto** o **Automático**.

1. Seleccione **Aceptar**.

   ![Habilitación de la depuración en modo mixto](../debugger/media/dbg-mixed-mode-from-native.png "Habilitación de la depuración en modo mixto")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Habilitación de la depuración en modo mixto para una aplicación de llamadas administrada

1. Seleccione el proyecto de C# o Visual Basic en **Explorador de soluciones**, seleccione el icono **Propiedades** y presione **Alt**+**Entrar**, o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Depurar** y, a continuación, seleccione **Habilitar depuración de código nativo**.

1. Cierre la página de propiedades para guardar los cambios.

   ![Habilitar depuración de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Habilitar depuración de código nativo")

> [!NOTE]
> En la mayoría de las versiones de Visual Studio a partir de Visual Studio 2017, debe usar el archivo *launchSettings.json* en lugar de las propiedades del proyecto para habilitar la depuración en modo mixto para el código nativo de una aplicación .NET Core. Para obtener más información, consulte [Tutorial: Depuración de C# y C++ en la misma sesión de depuración](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vea también

- [Cómo: Depuración desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)