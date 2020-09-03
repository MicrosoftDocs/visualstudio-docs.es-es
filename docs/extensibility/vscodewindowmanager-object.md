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
ms.openlocfilehash: 17bc9462af55ec9621654bd39cd65a2091f3f73f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740420"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

El servicio de lenguaje implementa el administrador de ventanas de código y es responsable de administrar los elementos gráficos (por ejemplo, la barra desplegable). Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

En la tabla siguiente se muestran las interfaces en el `VSCodeWindowManager` objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite agregar o quitar elementos gráficos (como barras desplegables) en una ventana de código.|
