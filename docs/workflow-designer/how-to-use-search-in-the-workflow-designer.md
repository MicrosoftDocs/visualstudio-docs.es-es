---
title: 'Cómo: usar la búsqueda en el Diseñador de flujo de trabajo | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d401f4061c142a739e4fa4215a401922b9e362
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Usar una búsqueda en el Diseñador de flujo de trabajo
Para facilitar la creación de flujos de trabajo mayores y más complejos, se puede usar Search en el diseñador de flujo de trabajo para encontrar elementos por palabra clave. Observe que el diseñador no admite Replace. La búsqueda buscará lo siguiente en el diseñador:  
  
## <a name="quick-find"></a>Búsqueda rápida  
 La búsqueda rápida buscará lo siguiente en el diseñador:  
  
-   Propiedades de los objetos <xref:System.Activities.Activity>, objetos <xref:System.Activities.Statements.FlowNode>, objetos <xref:System.Activities.Statements.State>, transiciones, así como otros elementos de control de flujo personalizados.  
  
-   Variables  
  
-   Argumentos  
  
-   Expresiones  
  
#### <a name="using-quick-find"></a>Usar Búsqueda rápida  
  
1.  Con el Diseñador de flujo de trabajo abierto, presione **CTRL+f**, o seleccione **editar**, **buscar y reemplazar**, **búsqueda rápida**.  
  
2.  Escriba el término de búsqueda en el **buscar** cuadro de texto y haga clic en **Buscar siguiente**.  
  
3.  El término de búsqueda se encontrará en el flujo de trabajo actual. La captura de pantalla siguiente muestra un nombre para mostrar de la actividad en el diseñador.  
  
     ![Resultado de búsqueda en el Diseñador de flujo de trabajo](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Buscar en archivos  
 Al usar Buscar en archivos se buscarán cadenas en archivos de flujo de trabajo, incluidos archivos XAML.  
  
#### <a name="using-find-in-files"></a>Usar Buscar en archivos  
  
1.  En Visual Studio, presione **Ctrl + Mayús + F**, o seleccione **editar**, **buscar y reemplazar**, **buscar en archivos**  
  
2.  Escriba el elemento que se busca en el **buscar** cuadro de texto y haga clic en **buscar todos**  
  
3.  Resultado de la búsqueda se mostrarán en el [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] **resultado de la búsqueda** vista. Al hacer doble clic, un elemento de resultado navegará a la actividad que contiene la coincidencia en el diseñador de flujo de trabajo.