---
title: Agregar extensiones a definiciones DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159080"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensión de la definición de DSL permite crear un paquete de extensiones para un lenguaje específico de dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), puede instalarse en el equipo del usuario en la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar en tiempo de ejecución dinámicamente. DSL no tiene que estar diseñado explícitamente para la extensión y las extensiones pueden diseñarse más adelante o por terceros sin alterar el DSL extendido.  
  
 Las características adicionales pueden incluir lo siguiente:  
  
- Propiedades de elementos de modelo y la presentación  
  
- Elementos Decorator para formas y conectores  
  
- Las clases, relaciones, formas y conectores  
  
- Restricciones de validación  
  
- Pestañas y elementos de cuadro de herramientas  
  
  Puede crear y guardar un modelo que contiene las instancias de las características adicionales de un usuario de un DSL extendido, y estos se pueden leer por otros usuarios que tengan instalada la extensión adecuada. Los usuarios que no tengan instalada la extensión no pueden usar las características adicionales, pero puede actualizar y guardar un modelo sin perder las características adicionales.  
  
  Código de ejemplo y obtener más información sobre esta característica, consulte el [Visual Studio SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128) sitio Web.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de Visual Studio y SDK de modelado](http://go.microsoft.com/fwlink/?LinkID=186128)
