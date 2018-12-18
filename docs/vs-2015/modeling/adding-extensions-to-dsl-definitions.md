---
title: Agregar extensiones a definiciones DSL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9c3e74f66edc0a8b33ad1fe8205cc02cd0e80054
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866160"
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



