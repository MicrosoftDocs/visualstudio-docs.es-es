---
title: Agregar extensiones a definiciones de DSL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="adding-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL
Extensión de definición DSL permite crear un paquete de extensiones en un lenguaje específico de dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo del usuario de la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar en tiempo de ejecución de dinámicamente. DSL no tienen que diseñarse explícitamente para la extensión y extensiones pueden diseñarse más adelante o por terceros sin modificar DSL extendida.  
  
 Las características adicionales pueden incluir lo siguiente:  
  
-   Propiedades de elementos de modelo y la presentación  
  
-   Decoradores para formas y conectores  
  
-   Las clases, relaciones, formas y conectores  
  
-   Restricciones de validación  
  
-   Pestañas y elementos de cuadro de herramientas  
  
 Un usuario de un DSL extendido puede crear y guardar un modelo que contiene las instancias de las características adicionales, y estos se pueden leer por otros usuarios que tengan instalada la extensión adecuada. Los usuarios que no se han instalado la extensión no pueden usar las características adicionales, pero puede actualizar y guardar un modelo sin perder las características adicionales.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también  
 [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
