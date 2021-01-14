---
title: Referencia de API del controlador | Microsoft Docs
description: Los visualizadores muestran un tipo específico de elemento de datos y también pueden permitir la edición. Para crear uno, use la API del visualizador que se documenta en esta sección.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- APIs, visualizers
- reference, visualizer APIs
- visualizers, API reference
ms.assetid: b9ff4ed0-9e80-49df-9016-a81189319afd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37346c77b1488bb89ac071a0290f7b5219731591
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149773"
---
# <a name="visualizer-api-reference"></a>Referencia de la API del visualizador

Las API del visualizador se proporcionan a usuarios que desean escribir un visualizador para el depurador de Visual Studio. Un visualizador es una aplicación pequeña que extiende la funcionalidad del la interfaz de usuario del depurador de Visual Studio. Un visualizador puede mostrar (y, opcionalmente, editar) un objeto de datos de un tipo específico para el que se diseña el visualizador.

## <a name="in-this-section"></a>En esta sección

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource?displayProperty=fullName>

## <a name="see-also"></a>Vea también

- [Tutorial: Escritura de un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Cómo: Escritura de un visualizador](create-custom-visualizers-of-data.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)