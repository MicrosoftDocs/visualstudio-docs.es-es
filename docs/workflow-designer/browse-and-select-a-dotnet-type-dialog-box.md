---
title: "Examinar y seleccionar un cuadro de diálogo de tipo .NET | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: "13"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: dotnet
ms.openlocfilehash: b891f2af72de34c2ccd71043f2674c338ddb44f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET
En el **propiedades** ventana, cuadros de diálogo o diseñadores como el Diseñador de variables, cuando se selecciona **buscar tipos...**  desde una lista de tipos de datos, es el **examinar y seleccionar un tipo .NET** cuadro de diálogo (denominado en forma abreviada como "tipo de explorador"). En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de ensamblados y proyectos.  
  
 Este cuadro de diálogo se emplea en varios escenarios de usuario, lo cual incluye lo siguiente:  
  
-   Cuando se establece el tipo de una variable o argumento.  
  
-   Cuando se selecciona un tipo para una actividad genérica.  
  
-   Cuando se agrega una instrucción catch en la actividad <xref:System.Activities.Statements.TryCatch>.  
  
> [!NOTE]
>  El explorador de tipo puede mostrar tipos de matrices escalonadas Visual Basic de matriz, pero no tipos de matrices multidimensionales. Vea [matrices escalonadas](http://go.microsoft.com/fwlink/?LinkId=195226) y [matrices multidimensionales](http://go.microsoft.com/fwlink/?LinkId=195227) para obtener más información.  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
1.  En el **nombre de tipo** cuadro, escriba el nombre del tipo que se va a utilizar.  
  
2.  Realice una de las siguientes acciones:  
  
    -   Cuando aparezca el nombre del tipo que se va a utilizar en el árbol en el **nombre de tipo** cuadro, haga doble clic en el tipo para seleccionarlo.  
  
    -   Escriba los caracteres suficientes en el **nombre de tipo** cuadro para identificar de forma única el tipo que desea usar y, a continuación, presione ENTRAR para seleccionar el tipo  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para seleccionar un tipo genérico en el explorador de tipo  
  
1.  En el **nombre de tipo** cuadro, escriba el nombre del tipo que se va a utilizar.  
  
2.  Cuando aparezca el nombre del tipo que se va a utilizar en el árbol en el **nombre de tipo** cuadro, haga clic en el tipo para seleccionarlo y cuadros de lista desplegable de que aparezcan.  
  
     Seleccione el tipo que desea utilizar para cerrar el genérico en los cuadros de lista desplegable y, a continuación, haga clic en **Aceptar**.  
  
## <a name="types-displayed-in-the-type-browser"></a>Tipos que se muestran en el explorador de tipo  
 Los tipos que se muestran en el explorador pueden variar en función de cómo se haya iniciado el explorador de tipo. Si el Explorador de tipo se ha iniciado desde un proyecto de flujo de trabajo dentro de **vs2010**, de forma predeterminada todos los tipos en los ensamblados de referencia y se muestran los proyectos que se hace referencia. Si el Explorador de tipo se ha iniciado desde fuera de un **vs2010** sistema (por ejemplo, como en una aplicación de flujo de trabajo hospedado en otro host o en un archivo de flujo de trabajo independiente), de proyectos, a continuación, de forma predeterminada se muestran los tipos de todos los ensamblados cargados en el dominio de aplicación .  
  
 Los tipos en el explorador de tipo se pueden filtrar por desarrolladores de software del diseñador de actividades. Respecto a una actividad en concreto, es posible que vea únicamente un subconjunto de los tipos. Por ejemplo, en la actividad <xref:System.Activities.Statements.TryCatch>, solo se muestran los tipos derivados de <xref:System.Exception> en el explorador de tipo.  
  
## <a name="filtering-search-results-in-the-type-browser"></a>Filtrar los resultados de la búsqueda en el explorador de tipo  
 La lista de tipos en el **nombre de tipo** cuadro reduciendo según se escriben más caracteres para encontrar una coincidencia. Solo aparecerán en la lista filtrada los tipos cuyo nombre completo o cuyo nombre corto comiencen con la cadena que ha escrito.  
  
 Por ejemplo:  
  
1.  Escriba **operación** coincide con <xref:System.OperationCanceledException> pero no <xref:System.InvalidOperationException>. Para buscar coincidencias con <xref:System.InvalidOperationException>, comience a escribir System.I o Invalid.  
  
2.  Escriba **genérico** coincide con <xref:System.GenericUriParser> , pero no con los tipos en el <xref:System.Collections.Generic> espacio de nombres. Para buscar tipos en el espacio de nombres <xref:System.Collections.Generic>, escriba el nombre completo del espacio de nombres.  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Seleccionar un contrato de servicio usando el cuadro de diálogo de explorador de tipo  
 Al seleccionar un tipo de contrato de servicio, el explorador de tipo muestra únicamente los tipos que tienen el atributo <xref:System.ServiceModel.ServiceContractAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)