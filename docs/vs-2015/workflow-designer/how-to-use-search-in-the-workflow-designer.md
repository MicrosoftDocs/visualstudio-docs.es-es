---
title: Filtrar Usar la búsqueda en el Diseñador de flujo de trabajo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 427e854c19e65463abcd8780cfe95d38f3ea66f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997675"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Filtrar Usar una búsqueda en el Diseñador de flujo de trabajo
Para facilitar la creación de flujos de trabajo mayores y más complejos, se puede usar Search en el diseñador de flujo de trabajo para encontrar elementos por palabra clave. Observe que el diseñador no admite Replace. La búsqueda buscará lo siguiente en el diseñador:  
  
## <a name="quick-find"></a>Búsqueda rápida  
 La búsqueda rápida buscará lo siguiente en el diseñador:  
  
-   Propiedades de los objetos <xref:System.Activities.Activity>, objetos <xref:System.Activities.Statements.FlowNode>, objetos <xref:System.Activities.Statements.State>, transiciones, así como otros elementos de control de flujo personalizados.  
  
-   Variables  
  
-   Argumentos  
  
-   Expresiones  
  
#### <a name="using-quick-find"></a>Usar Búsqueda rápida  
  
1.  Con el Diseñador de flujo de trabajo abierto, presione **CTRL+f**, o bien seleccione **editar**, **buscar y reemplazar**, **búsqueda rápida**.  
  
2.  Escriba el término de búsqueda en el **buscar** cuadro de texto y haga clic en **Buscar siguiente**.  
  
3.  El término de búsqueda se encontrará en el flujo de trabajo actual. La captura de pantalla siguiente muestra un nombre para mostrar de la actividad en el diseñador.  
  
     ![Resultado de búsqueda en el Diseñador de flujo de trabajo](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Buscar en archivos  
 Al usar Buscar en archivos se buscarán cadenas en archivos de flujo de trabajo, incluidos archivos XAML.  
  
#### <a name="using-find-in-files"></a>Usar Buscar en archivos  
  
1.  En Visual Studio, presione **Ctrl + Mayús + F**, o bien seleccione **editar**, **buscar y reemplazar**, **buscar en archivos**  
  
2.  Escriba el elemento de búsqueda en el **buscar** cuadro de texto y haga clic en **Buscar todo**  
  
3.  Resultado de la búsqueda se mostrará en el [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **resultado de la búsqueda** vista. Al hacer doble clic, un elemento de resultado navegará a la actividad que contiene la coincidencia en el diseñador de flujo de trabajo.