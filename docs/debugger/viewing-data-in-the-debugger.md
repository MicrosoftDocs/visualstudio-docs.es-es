---
title: Crear vistas personalizadas de los datos en el depurador | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568991"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Crear vistas personalizadas de los datos en el depurador deC#Visual Studio ( C++, Visual Basic,)

El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona muchas herramientas para inspeccionar y modificar el estado del programa. La mayoría de estas herramientas sólo funcionan en el modo de interrupción.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Crear vistas personalizadas de los datos en ventanas de variables y en información sobre datos

 Muchas de las [ventanas del depurador](../debugger/debugger-windows.md), como las ventanas **automático** y **inspección** , permiten inspeccionar las variables. Puede personalizar el modo C++ en que se muestran los tipos, objetos administrados y sus propios tipos en las ventanas de variables del depurador y en la [información sobre herramientas](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Para obtener más información, vea [crear vistas personalizadas C++ de objetos](../debugger/create-custom-views-of-native-objects.md) y [crear vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Crear visualizadores personalizados

 Los visualizadores permiten ver el contenido de un objeto o una variable de forma significativa. En el depurador de Visual Studio, un visualizador hace referencia a las distintas ventanas que se pueden abrir con el icono de ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador") de lupa. Por ejemplo, el visualizador HTML muestra cómo una cadena HTML se interpretaría y se mostraría en un explorador. Puede tener acceso a los visualizadores desde información sobre herramientas, la ventana **inspección** , la ventana **automático** y la ventana **variables locales** . El cuadro de diálogo **Inspección rápida** también proporciona un visualizador. Para obtener más información, vea [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Ventana Comandos](../ide/reference/command-window.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
