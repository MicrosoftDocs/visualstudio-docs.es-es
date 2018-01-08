---
title: "Implementación de Shell de VS | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell
Un shell aislado permite determinar qué Visual Studio funcionalidad que necesita para interactuar con el lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, vea [personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md). Puede encontrar más información sobre cómo personalizar el shell aislado en [personalizar el Shell aislado](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un Shell de Visual Studio como el destino de implementación  
  
1.  En el **DslPackage** proyecto abierto **source.extension.tt**.  
  
2.  En `<SupportedProducts>` insertar:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Reemplace *MyIsolatedShell* con el nombre de su paquete de shell aislado.