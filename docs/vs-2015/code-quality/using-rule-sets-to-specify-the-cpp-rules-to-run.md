---
title: Usar conjuntos de reglas para especificar las reglas de C++ en ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9466bf421ca5844d3d7083528fb1a27e3c488937
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567199"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [utilizando conjuntos de reglas para especificar las reglas de C++ para ejecutar](https://docs.microsoft.com/visualstudio/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).  
  
En [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] y [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], puede crear y modificar una personalizada *conjunto de reglas* para satisfacer las necesidades concretas del proyecto asociadas con el análisis de código. Para crear una regla personalizada de C++ establece, un proyecto de C o C++ debe estar abierto en el IDE de Visual Studio. Y, a continuación, abra un conjunto de reglas estándar en el editor de conjunto de reglas, a continuación, agregar o quitar reglas concretas y, opcionalmente, cambiar la acción que se produce cuando el análisis de código determina que se ha infringido una regla.  
  
 Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.  
  
## <a name="opening-the-rule-set-editor"></a>Abrir el editor de conjuntos de reglas  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente  
  
1.  En el Explorador de soluciones, abra el menú contextual para el proyecto y, a continuación, elija **propiedades**.  
  
2.  En el **propiedades** ficha, elija **análisis de código**.  
  
3.  En el **Pravidel** lista desplegable, realice una de las siguientes acciones:  
  
    -   Elija el conjunto de reglas que desea personalizar.  
  
     \- o -  
  
    -   Elija  **\<Examinar... >** especificar una regla existente conjunto que no está en la lista.  
  
4.  Elija **abierto** para mostrar las reglas en el editor de conjunto de reglas.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas  
  
-   Para cambiar el nombre para mostrar del conjunto de reglas, en el **vista** menú, elija **ventana propiedades**. Escriba el nombre para mostrar en el **nombre** cuadro. Observe que el nombre para mostrar puede diferir del nombre de archivo.  
  
-   Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.  
  
-   Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.  
  
-   Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, elija el **acción** por la regla de campo y, a continuación, elija uno de los valores siguientes:  
  
     **Advertir** -genera una advertencia.  
  
     **Error** -genera un error.  
  
     **Ninguno** -deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor  
  
-   Para expandir las reglas en todos los grupos, elija **Expandir todo**.  
  
-   Para contraer las reglas en todos los grupos, elija **Contraer todo**.  
  
-   Para cambiar el campo que las reglas se agrupan por, elija el campo desde el **Group By** lista. Para mostrar las reglas desagrupadas, seleccione  **\<None >**.  
  
-   Para agregar o quitar campos en las columnas de la regla, elija **opciones de columna**.  
  
-   Para ocultar reglas que no se aplican a la solución actual, elija **ocultar reglas que no se aplican a la solución actual**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la acción de Error, elija **Mostrar reglas que pueden generar errores de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignadas la acción advertencia, elija **Mostrar reglas que pueden generar advertencias de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la **ninguno** acción, elija **Mostrar reglas no habilitadas**.  
  
-   Para agregar o quitar conjuntos de reglas predeterminados para el conjunto de reglas actual de Microsoft, elija **agregar o quitar conjuntos de reglas secundarios**.



