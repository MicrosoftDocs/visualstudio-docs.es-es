---
title: Buscar posibles problemas mediante analizadores de mapas de código
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e300603280b6c0b57d7397699786f2d3c6ff8317
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33872814"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Buscar posibles problemas mediante analizadores de mapas de código

Ejecute analizadores en mapas de código para identificar código demasiado complejo o que sea necesario mejorar. Por ejemplo, puede usar estos analizadores:

|**Para buscar código que incluya**|**Examine estas áreas para ver si:**|
|-------------------------------|--------------------------------------------|
|Bucles o dependencias circulares|Puede simplificarlos y ver si puede interrumpir estos ciclos.|
|Demasiadas dependencias|Están realizando demasiadas funciones o determinan el impacto de cambiar estas áreas. En un mapa de código correcto, aparecerá un número mínimo de dependencias. Para que el código resulte más fácil de mantener, cambiar, probar y reutilizar, piense si puede refactorizar estas áreas para definirlas de forma más nítida o si puede combinar el código que realiza funciones similares.|
|Ninguna dependencia|Son necesarias o si debe quitar este código.|

## <a name="analyze-code-maps"></a>Analizar mapas de código

En la barra de herramientas del mapa, elija **diseño** > **analizadores**y, a continuación, el analizador que desea ejecutar:

|**Analizador**|**Para identificar nodos que**|
|------------------|--------------------------------|
|**Analizador de referencias circulares**|Tienen dependencias circulares entre sí. **Nota:** dependencias circulares que se encuentran en el **genéricos** grupo no se muestran en el mapa al expandir el grupo.|
|**Buscar analizador de concentradores**|Se encuentran entre el 25 % de los nodos con mayor número de conexiones.<br /><br /> **Para ocultar el resto de nodos del mapa**<br /><br /> : Abre el menú contextual del mapa, elija **avanzadas**, **seleccione**, **ocultar no seleccionados**.<br />     El mapa oculta los nodos no seleccionados y el analizador identifica los nuevos nodos como concentradores.|
|**Analizador de nodos a los que no se hace referencia**|No tienen referencias de otros nodos. **Precaución:** compruebe cada uno de estos casos antes de asumir que no se usa el código. Ciertas dependencias, como las dependencias XAML y las dependencias de tiempo de ejecución, no se encuentran de forma estática en el código.|

Los analizadores de mapa de código continuarán ejecutándose después de aplicarlos. Si cambia el mapa, los analizadores aplicados volverán a procesar automáticamente el mapa actualizado. Para detener la ejecución de un analizador, en la barra de herramientas del mapa, elija **diseño** > **analizadores**. Desactive el analizador seleccionado.

> [!TIP]
> Si tiene un mapa muy grade y ejecuta el analizador, podría producirse una excepción de memoria. Si esto ocurre, edite el mapa para reducir su ámbito o genere uno más pequeño y, después, ejecute el analizador.

## <a name="see-also"></a>Vea también

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
