---
title: Implementación de VS Shell | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 323dd1242dcc598b5f30fdd24f37e305712d4d78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172918"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un shell aislado le permite determinar qué Visual Studio funcionalidad que necesita para interactuar con su lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, consulte [personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md). Puede encontrar más información sobre cómo personalizar el shell aislado en [personalización del Shell aislado](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un Shell de Visual Studio como el destino de implementación  
  
1.  En el **DslPackage** proyecto, abra **source.extension.tt**.  
  
2.  Bajo `<SupportedProducts>` insertar:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Reemplace *MyIsolatedShell* con el nombre del paquete de shell aislado.



