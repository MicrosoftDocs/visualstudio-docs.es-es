---
title: Objeto VSCodeWindowManager | Microsoft Docs
description: Obtenga información sobre el objeto VSCodeWindowManager, que es responsable de administrar los adornos, por ejemplo, la barra desplegable.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 76ab3d2a72c957b20a79850dc312f5c16de98afc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905299"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

El servicio de lenguaje implementa el administrador de ventanas de código y es responsable de administrar los adornos (por ejemplo, la barra desplegable). Para obtener más información, consulte [Personalización de ventanas de código mediante la API heredada.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

En la tabla siguiente se muestran las interfaces del `VSCodeWindowManager` objeto .

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite agregar o quitar adornos (por ejemplo, barras desplegables) en una ventana de código o quitarse de esta.|