---
title: Buscar posibles problemas mediante analizadores de mapas de código
description: Obtenga información sobre cómo puede ejecutar analizadores en mapas de código para ayudarle a identificar código que podría ser demasiado complejo o que podría necesitar una mejora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388859"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Buscar posibles problemas mediante analizadores de mapas de código

Ejecute analizadores en mapas de código para identificar código demasiado complejo o que sea necesario mejorar. Por ejemplo, puede usar estos analizadores:

|**Para buscar código que incluya**|**Examine estas áreas para ver si:**|
|-|-|
|Bucles o dependencias circulares|Puede simplificarlos y ver si puede interrumpir estos ciclos.|
|Demasiadas dependencias|Están realizando demasiadas funciones o determinan el impacto de cambiar estas áreas. En un mapa de código correcto, aparecerá un número mínimo de dependencias. Para que el código resulte más fácil de mantener, cambiar, probar y reutilizar, piense si puede refactorizar estas áreas para definirlas de forma más nítida o si puede combinar el código que realiza funciones similares.|
|Ninguna dependencia|Son necesarias o si debe quitar este código.|

## <a name="analyze-code-maps"></a>Analizar mapas de código

En la barra de herramientas del mapa, elija **Analizadores** de diseño y, a continuación, el analizador  >  que desea ejecutar:

|**Analyzer**|**Para identificar nodos que**|
|-|-|
|**Analizador de referencias circulares**|Tienen dependencias circulares entre sí. **Nota:**  Las dependencias circulares que están **en el grupo Genéricos** no se muestran en el mapa al expandir el grupo.|
|**Buscar analizador de concentradores**|Se encuentran entre el 25 % de los nodos con mayor número de conexiones.<br /><br /> **Para ocultar el resto de nodos del mapa**<br /><br /> - Abra el menú contextual del mapa, elija **Opciones** avanzadas , **Seleccionar**, **Ocultar sin seleccionar.**<br />     El mapa oculta los nodos no seleccionados y el analizador identifica los nuevos nodos como concentradores.|
|**Analizador de nodos a los que no se hace referencia**|No tienen referencias de otros nodos. **Precaución:**  Compruebe cada uno de estos casos antes de suponer que no se usa el código. Ciertas dependencias, como las dependencias XAML y las dependencias de tiempo de ejecución, no se encuentran de forma estática en el código.|

Los analizadores de mapa de código continuarán ejecutándose después de aplicarlos. Si cambia el mapa, los analizadores aplicados volverán a procesar automáticamente el mapa actualizado. Para dejar de ejecutar un analizador, en la barra de herramientas del mapa, elija  >  **Analizadores de diseño**. Desactive el analizador seleccionado.

> [!TIP]
> Si tiene un mapa muy grade y ejecuta el analizador, podría producirse una excepción de memoria. Si esto ocurre, edite el mapa para reducir su ámbito o genere uno más pequeño y, después, ejecute el analizador.

## <a name="see-also"></a>Vea también

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
