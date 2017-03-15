---
title: Agregar extensiones a definiciones DSL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL
Extensión de la definición de DSL permite crear un paquete de extensiones de un lenguaje específico de dominio (DSL). La extensión DSL, que está contenida en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo del usuario de la misma manera que un DSL. Las características adicionales pueden habilitar y deshabilitar en tiempo de ejecución dinámicamente. DSL no tiene que ser diseñado explícitamente para la extensión y las extensiones pueden diseñarse más adelante o por terceros sin alterar el DSL extendido.  
  
 Las características adicionales pueden incluir lo siguiente:  
  
-   Propiedades de elementos de modelo y la presentación  
  
-   Elementos Decorator para formas y conectores  
  
-   Clases, relaciones, formas y conectores  
  
-   Restricciones de validación  
  
-   Fichas y elementos del cuadro de herramientas  
  
 Un usuario de un DSL extendido puede crear y guardar un modelo que contiene instancias de las características adicionales, y éstos se pueden leer por otros usuarios que hayan instalado la extensión adecuada. Los usuarios que no se han instalado la extensión no pueden utilizar las características adicionales, pero puede actualizar y guardar un modelo sin perder las características adicionales.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también  
 [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

