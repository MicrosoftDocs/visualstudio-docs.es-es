---
title: Objeto VSCodeWindowManager | Microsoft Docs
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
ms.openlocfilehash: fea97c8784402c55947c108f42f2f3153f322d9c
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012391"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

El servicio de lenguaje implementa el administrador de ventanas de código y es responsable de administrar los elementos gráficos (por ejemplo, la barra desplegable). Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

En la tabla siguiente se muestran las interfaces en el `VSCodeWindowManager` objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite agregar o quitar elementos gráficos (como barras desplegables) en una ventana de código.|