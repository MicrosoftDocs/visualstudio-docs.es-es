---
title: Agregar extensiones a definiciones de DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c5968fccb55a265639ff05c600bd5f97a9f90a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852105"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La extensión DSL Definition le permite crear un paquete de extensiones para un lenguaje específico del dominio (DSL). La extensión DSL, que se encuentra en una extensión de integración de Visual Studio (VSIX), se puede instalar en el equipo de un usuario de la misma manera que un DSL. Las características adicionales se pueden habilitar y deshabilitar dinámicamente en tiempo de ejecución. Los DSL no tienen que diseñarse explícitamente para la extensión, y las extensiones se pueden diseñar posteriormente o por terceros sin modificar el DSL extendido.

 Entre las características adicionales se incluyen las siguientes:

- Propiedades de los elementos de modelo y presentación

- Elementos Decorator para formas y conectores

- Clases, relaciones, formas y conectores

- Restricciones de validación

- Elementos y pestañas del cuadro de herramientas

  Un usuario de un DSL extendido puede crear y guardar un modelo que contenga instancias de las características adicionales, y otros usuarios que hayan instalado la extensión adecuada podrán leerlos. Los usuarios que no han instalado la extensión no pueden usar las características adicionales, pero pueden actualizar y guardar un modelo sin perder las características adicionales.

  Para obtener código de ejemplo y más información acerca de esta característica, vea el sitio web del [SDK de visualización y modelado de Visual Studio](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) .

## <a name="see-also"></a>Vea también
 [SDK de visualización y modelado de Visual Studio](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)
