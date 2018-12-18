---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566678"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué Visual Studio funcionalidad que necesita para interactuar con su lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, consulte [personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un Shell de Visual Studio como el destino de implementación

1.  En el **DslPackage** proyecto, abra **source.extension.tt**.

2.  Bajo `<SupportedProducts>` insertar:

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Reemplace *MyIsolatedShell* con el nombre del paquete de shell aislado.