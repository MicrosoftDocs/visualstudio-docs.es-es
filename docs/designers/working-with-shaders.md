---
title: Trabajar con sombreadores
description: Aprenda a diseñar efectos de sombreador personalizados mediante el Diseñador de sombras basado en gráficos en Visual Studio. Estos sombreadores se pueden usar en su aplicación o juego basado en DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bff5aee4337a464498fc4ac027eb05b2da912b61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844897"
---
# <a name="work-with-shaders"></a>Trabajar con sombreadores

Puede usar el Diseñador de sombras basado en gráficos de Visual Studio para diseñar efectos de sombreador personalizados. Estos sombreadores se pueden usar en la aplicación o juego basado en DirectX.

## <a name="shaders"></a>Sombreadores

Un *sombreador* es un programa informático que realiza cálculos de gráficos (por ejemplo, transformaciones de vértice o coloreado de píxeles) y que suele ejecutarse en una unidad de procesamiento gráfico (GPU) en lugar de en la CPU. Dado que ahora la mayoría de las etapas de la canalización tradicional de gráficos de función fija se efectúa con programas de sombreador, puede usarlos para crear una canalización que sea específica para las necesidades de su aplicación.

Los tipos más comunes de sombreador son los *sombreadores de vértices* (que realizan cálculos por vértice y reemplazan la transformación de función fija y el circuito de iluminación en hardware de gráficos no programable) y los *sombreadores de píxeles* (que realizan cálculos por píxel con los que se determina el color de un píxel y se reemplaza el circuito de combinación de colores de función fija en el hardware de gráficos no programable). El hardware gráfico actual ha hecho posible todavía más tipos de sombreadores; así, los *sombreadores de casco*, los *sombreadores de dominio* y los *sombreadores de geometría* para realizar cálculos de gráficos, o los *sombreadores de proceso* para realizar cálculos no gráficos. Ninguna de estas fases está disponible en el hardware de gráficos no programable. En principio, los sombreadores se crearon con un lenguaje parecido al de los ensamblados que proporcionaba instrucciones paralelas a datos (SIMD) y centradas en gráficos (producto de puntos). Ahora, los sombreadores se suelen crear con lenguajes tipo C de alto nivel como HLSL (High Level Shader Language, lenguaje de sombreado de alto nivel).

El Diseñador de sombras se puede usar para crear sombreadores de píxeles de forma interactiva, en lugar de tener que escribir y compilar código. En el Diseñador de sombras, un sombreador se define a partir de un número de nodos que representan datos y operaciones, y de las conexiones entre los nodos que representan el flujo de valores de datos y los resultados intermedios a través del sombreador. Si se emplea este método y la vista previa en tiempo real del Diseñador de sombras, se puede visualizar la ejecución del sombreador más fácilmente, así como experimentar para "detectar" variaciones de sombreador interesantes.

## <a name="dgsl-documents"></a>Documentos DGSL

El Diseñador de sombras guarda los sombreadores con el formato Directed Graph Shader Language (DGSL), que es un formato XML basado en el lenguaje Directed Graph Markup Language (DGML). Los sombreadores DGSL se pueden usar directamente en los modelos 3D del editor de modelos. Pero, para poder usar un sombreador DGSL en la aplicación, antes hay que exportarlo a un formato que DirectX entienda (HLSL, por ejemplo).

Como DGSL es compatible con DGML, puede usar herramientas diseñadas para analizar documentos DGML con el propósito de analizar sombreadores DGSL. Para más información sobre DGML, vea [Understanding Directed Graph Markup Language (DGML)](../modeling/customize-code-maps-by-editing-the-dgml-files.md) (Introducción a Directed Graph Markup Language [DGML]).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Diseñador de sombras](../designers/shader-designer.md)|Describe cómo usar el diseñador de sombras de Visual Studio para trabajar con sombreadores.|
|[Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)|Se abordan los tipos de nodos del Diseñador de sombras que se pueden usar para lograr efectos gráficos.|
|[Ejemplos del Diseñador de sombras](../designers/how-to-create-a-basic-color-shader.md)|Aquí encontrará vínculos a temas donde se explica cómo usar el Diseñador de sombras para lograr efectos gráficos comunes.|
