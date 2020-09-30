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
ms.openlocfilehash: 9668336c565b4a3be332509d1c960b067a486785
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583637"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

El servicio de lenguaje implementa el administrador de ventanas de código y es responsable de administrar los elementos gráficos (por ejemplo, la barra desplegable). Para obtener más información, vea [personalizar ventanas de código mediante la API heredada](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

En la tabla siguiente se muestran las interfaces en el `VSCodeWindowManager` objeto.

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite agregar o quitar elementos gráficos (como barras desplegables) en una ventana de código.|