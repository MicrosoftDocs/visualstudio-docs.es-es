---
title: Objeto VSCodeWindowManager | Microsoft Docs
description: Obtenga información sobre el objeto VSCodeWindowManager, que es responsable de administrar los elementos gráficos, por ejemplo, la barra desplegable.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863992"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

El servicio de lenguaje implementa el administrador de ventanas de código y es responsable de administrar los elementos gráficos (por ejemplo, la barra desplegable). Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

En la tabla siguiente se muestran las interfaces en el `VSCodeWindowManager` objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite agregar o quitar elementos gráficos (como barras desplegables) en una ventana de código.|