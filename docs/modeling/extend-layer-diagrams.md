---
title: Ampliar diagramas de dependencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>Ampliar diagramas de dependencia
Puede escribir código para crear y actualizar diagramas de dependencia y validar la estructura del código del programa con diagramas de dependencia en Visual Studio. Puede agregar los comandos que aparecen en el menú contextual de los diagramas, personalizar gestos de arrastrar y colocar, así como obtener acceso al modelo de capas desde las plantillas de texto. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio (VSIX) y distribuirla a otros usuarios de Visual Studio.  
  
 Para obtener más información acerca de los diagramas de dependencia, vea:  
  
-   [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)  
  
-   [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)  
  
-   [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> Requisitos  
 Necesita tener instalado lo siguiente en el equipo donde desea desarrollar las extensiones de capa:  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modelar el SDK de Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Debe tener una versión adecuada de Visual Studio instalada en el equipo donde desea ejecutar las extensiones de capas. Para obtener más información, consulte [implementar una extensión del modelo de capas](../modeling/deploy-a-layer-model-extension.md).  
  
 Para ver qué versiones de Visual Studio admiten diagramas de dependencia, vea [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>En esta sección  
 [Agregar comandos y gestos a diagramas de dependencia](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Agregar validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Agregar propiedades personalizadas a diagramas de dependencia](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Navegar y actualizar modelos de capas en el código del programa](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Implementar una extensión del modelo de capas](../modeling/deploy-a-layer-model-extension.md)  
  
 [Solucionar problemas de extensiones para diagramas de dependencia](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Vea también  
 [Definir e instalar una extensión de modelado](../modeling/define-and-install-a-modeling-extension.md)   
 [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)   
 [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)   
 [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)   
 [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)   

