---
title: Implementación de VS Shell | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bfe88d7e7d742eb67273d307c3a8e72e9a85833
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704047"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un shell aislado le permite determinar qué Visual Studio funcionalidad que necesita para interactuar con su lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, consulte [personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md). Puede encontrar más información sobre cómo personalizar el shell aislado en [personalización del Shell aislado](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un Shell de Visual Studio como el destino de implementación  
  
1. En el **DslPackage** proyecto, abra **source.extension.tt**.  
  
2. Bajo `<SupportedProducts>` insertar:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Reemplace *MyIsolatedShell* con el nombre del paquete de shell aislado.
