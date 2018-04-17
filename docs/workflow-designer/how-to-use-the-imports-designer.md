---
title: 'Cómo: usar el Diseñador de importaciones | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94b55e4b9f7f2b1d4e571b11fcdc4fba4d4f6754
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-imports-designer"></a>Utilizar el diseñador de importaciones
El diseñador de importaciones le permite escribir los espacios de nombres para los tipos que utilizará en sus expresiones. Muy parecida a la **importa** o **con** habilitar palabras clave en Visual Basic y C#, especificar espacios de nombres en el Diseñador de importaciones le permite escribir simplemente un nombre de tipo en la expresión en lugar de un nombre completo nombre del tipo de versión.  
  
 El diseñador de importaciones reacciona tanto a los cambios en la interfaz de usuario como a los cambios que se efectúan cuando se guarda el flujo de trabajo. Cuando el flujo de trabajo está guardado, los espacios de nombres se pueden agregar automáticamente al diseñador de importaciones. Entre ellas se incluyen las siguientes:  
  
-   Espacios de nombres para cualquier tipo utilizado en declaraciones de variables y de argumentos.  
  
-   Espacios de nombres para cualquier tipo utilizado en expresiones.  
  
-   Cualquier otro espacio de nombres que se necesite para serializar el flujo de trabajo (por ejemplo, espacios de nombres utilizados por actividades personalizadas que se hayan colocado en el flujo de trabajo).  
  
 Cuando se guarda el flujo de trabajo, podría observar que algunos espacios de nombres que ha eliminado manualmente se vuelven a agregar automáticamente al diseñador de importaciones debido a la lógica descrita en la lista anterior.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Para agregar un espacio de nombres a la lista de espacios de nombres importados  
  
1.  Abra una aplicación de servicio de WCF, una aplicación de consola del flujo de trabajo, un proyecto de biblioteca de actividades en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] o una aplicación de flujo de trabajo hospedada en otro host.  
  
2.  Haga clic en **importaciones** en la parte inferior del lienzo principal. Aparecerá el diseñador de importaciones.  
  
3.  Escriba o seleccione un espacio de nombres desde el control de lista desplegable en la parte superior del diseñador de importaciones.  
  
     Cuando escriba, aparecerá una lista de espacios de nombres válidos que coinciden con los caracteres que se van escribiendo.  
  
4.  Presione **ENTRAR** para agregar el espacio de nombres a la lista.  
  
5.  Si desea quitar un espacio de nombres de la lista, seleccione el espacio de nombres y, a continuación, presione la **eliminar** clave en el teclado. Observe que un espacio de nombres solo se puede eliminar si el espacio de nombres no es válido por cualquier razón, por ejemplo si el proyecto ya no hace referencia al ensamblado que contiene el espacio de nombres.