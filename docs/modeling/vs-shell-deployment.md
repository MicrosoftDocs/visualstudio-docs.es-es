---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445004"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre el shell aislado de Visual Studio, vea [Personalizar el shell aislado](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Para establecer un Shell de Visual Studio como destino de implementación:

1. En el proyecto **DslPackage,** abra **source.extension.tt**.

2. En `<SupportedProducts>` insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* por el nombre del paquete de shell aislado.
