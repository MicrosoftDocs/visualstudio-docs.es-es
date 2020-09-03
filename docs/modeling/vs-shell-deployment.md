---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535855"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita para interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre el shell aislado de Visual Studio, vea [personalizar el shell aislado](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Para establecer un shell de Visual Studio como destino de implementación:

1. En el proyecto **DslPackage** , Abra **source.Extension.TT**.

2. En `<SupportedProducts>` Insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* por el nombre del paquete de Shell aislado.
