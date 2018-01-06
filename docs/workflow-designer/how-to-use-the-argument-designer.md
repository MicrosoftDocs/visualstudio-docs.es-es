---
title: "Cómo: usar el Diseñador de argumentos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aa1cdd0dd563a5f87d4e32f779985afd63319032
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-argument-designer"></a>Utilizar el diseñador de argumentos
Si se compara con las versiones anteriores de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], el diseñador de argumentos hace más fácil permitir el flujo de datos dentro y fuera de una actividad. El diseñador se tiene acceso haciendo clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de argumentos que aparecen en un formato tabular y pueden ordenarse por cada uno de los encabezados de columna, excepto para la **valor predeterminado** columna. Cada argumento contiene un nombre, dirección IN/OUT/IN-OUT/PROPERTY, tipo y valor de la expresión predeterminado (en su caso). El nombre y el valor de la expresión predeterminado son campos de texto editable y el tipo y la dirección son listas desplegables. [! INCLUIR[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
### <a name="to-create-a-new-argument"></a>Para crear un argumento nuevo  
  
1.  Abra un flujo de trabajo o solución de actividades en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Abra el Diseñador de argumentos, haga clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de argumentos.  
  
3.  Haga clic en la fila vacía con la etiqueta **crear argumento**. Esto agregará una nueva fila con un nuevo argumento mediante los siguientes valores predeterminados: argumentx para el **nombre** donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de argumento único, **en**  para el **dirección**, y **cadena** para el **tipo de argumento**. No se agrega ningún valor para **valor predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.  
  
    > [!NOTE]
    >  Para eliminar un argumento, seleccione el argumento haciendo clic en él y, a continuación, presione la **eliminar** clave.  
  
## <a name="see-also"></a>Vea también  
 [Mediante el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)   
 [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)