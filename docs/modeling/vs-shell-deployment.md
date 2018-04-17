---
title: Implementación de Shell de VS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4964ce162efac640ea7581b4d3f26f3d50087319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado permite determinar qué Visual Studio funcionalidad que necesita para interactuar con el lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, vea [personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un Shell de Visual Studio como el destino de implementación
  
1.  En el **DslPackage** proyecto abierto **source.extension.tt**.  
  
2.  En `<SupportedProducts>` insertar:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Reemplace *MyIsolatedShell* con el nombre de su paquete de shell aislado.