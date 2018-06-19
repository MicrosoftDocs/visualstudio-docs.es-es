---
title: 'Diseñador de flujo de trabajo: Cómo: depurar flujos de trabajo basados en ASP.NET (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975877"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Cómo: Depurar los flujos de trabajo basados en ASP.NET (Heredado)

En este tema se describe cómo depurar aplicaciones basadas en ASP.NET Windows Workflow Foundation (WF) que tienen como destino ya sea la versión de .NET Framework 3.5 o la WinFX en el Diseñador de flujo de trabajo de Windows heredado.

Puede depurar flujos de trabajo heredados que se inician en ASP.NET o flujos de trabajo heredados que se publican como servicio Web adjuntándolos al proceso en el que está hospedado el flujo de trabajo.

## <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar un flujo de trabajo basado en ASP.NET

1.  Habilitar la depuración de la aplicación ASP.NET estableciendo **debug = true** en el archivo web.config.

2.  Establezca la biblioteca de flujos de trabajo como proyecto de inicio y establezca puntos de interrupción en el flujo de trabajo.

3.  Escriba la dirección URL de la página Web predeterminada en las propiedades del proyecto de flujo de trabajo **depurar** opción **Iniciar explorador con la dirección URL** cuadro de texto.

4.  Seleccione **adjuntar al proceso** en el **depurar** menú.

5.  Seleccione el proceso para adjuntar a desde el **procesos disponibles** lista.

     Adjunte al w3wp.exe, webdev.webserver o al proceso de aspnet_wp en que está hospedado el flujo de trabajo.

6.  Haga clic en **seleccione** junto a la **adjuntar a** cuadro de texto.

     El **Seleccionar tipo de código** aparece el cuadro de diálogo.

7.  Seleccione **depurar estos tipos de código** y seleccione **flujo de trabajo**.

8.  Haga clic en **Aceptar**.

9. Haga clic en **Adjuntar**.

10. Abra la página web predeterminada en un explorador e inicie el flujo de trabajo.

## <a name="see-also"></a>Vea también

- [Invocar el Depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Cómo: Establecer puntos de interrupción en los flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)