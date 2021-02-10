---
title: Creación de vistas personalizadas de datos en el depurador | Microsoft Docs
description: Obtenga información sobre las distintas maneras de inspeccionar y modificar el estado de un programa en el depurador de Visual Studio. Entre ellas, se incluyen las ventanas Inspección y Automático, Información sobre datos y Visualizadores.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d51821597c68a9b8e0c97e4cac3c7dc7ec2b8cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884356"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Creación de vistas personalizadas de datos en el depurador de Visual Studio (C#, Visual Basic y C++)

El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona muchas herramientas para inspeccionar y modificar el estado de los programas. La mayoría de estas herramientas sólo funcionan en el modo de interrupción.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Creación de vistas personalizadas de datos en ventanas de variables y en Información sobre datos

 Muchas de las [ventanas del depurador](../debugger/debugger-windows.md), como **Automático** e **Inspección**, permiten inspeccionar las variables. Puede personalizar cómo se muestran los tipos de C++, los objetos administrados y sus propios tipos en las ventanas de variables del depurador y en [Información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Para obtener más información, vea [Creación de vistas personalizadas de objetos de C++](../debugger/create-custom-views-of-native-objects.md) y [Creación de vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Crear visualizadores personalizados

 Los visualizadores permiten ver de forma útil el contenido de un objeto o una variable. En el depurador de Visual Studio, un visualizador hace referencia a las distintas ventanas que se pueden abrir con el icono de lupa ![Icono del visualizador](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador"). Por ejemplo, en el visualizador HTML se muestra cómo se interpretaría y se mostraría una cadena HTML en un explorador. Puede acceder a los visualizadores desde Información sobre datos y las ventanas **Inspección**, **Automático** y **Variables locales**. En el cuadro de diálogo **Inspección rápida** también se proporciona un visualizador. Para obtener más información, vea [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Ventana Comandos](../ide/reference/command-window.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
