---
title: Implementación de VS Shell
description: Obtenga información sobre cómo un shell aislado le permite determinar Visual Studio funcionalidad que necesita para interactuar con el DSL y cómo debe aparecer esa solución.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388313"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué funcionalidad Visual Studio necesita para interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre Visual Studio shell aislado, vea [Personalización del shell aislado.](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

Para establecer un Visual Studio Shell como destino de implementación:

1. En el **proyecto DslPackage,** abra **source.extension.tt**.

2. En `<SupportedProducts>` insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* por el nombre del paquete de shell aislado.