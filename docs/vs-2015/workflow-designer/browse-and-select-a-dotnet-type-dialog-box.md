---
title: Examinar y seleccionar un cuadro de diálogo de tipo de .NET | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1bff5fccfbd4998e477043188c955e3446a45d69
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192541"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Examinar y seleccionar un cuadro de diálogo de tipo .NET
En el **propiedades** diseñadores como el Diseñador de variables, cuando se selecciona, los cuadros de diálogo o ventana **buscar tipos...** en una lista de tipos de datos, es el **examinar y seleccionar un tipo .NET** cuadro de diálogo (denominada en forma abreviada como "tipo de explorador"). En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de ensamblados y proyectos.  
  
 Este cuadro de diálogo se emplea en varios escenarios de usuario, lo cual incluye lo siguiente:  
  
-   Cuando se establece el tipo de una variable o argumento.  
  
-   Cuando se selecciona un tipo para una actividad genérica.  
  
-   Cuando se agrega una instrucción catch en la actividad <xref:System.Activities.Statements.TryCatch>.  
  
> [!NOTE]
>  El explorador de tipo puede mostrar tipos de matrices escalonadas Visual Basic de matriz, pero no tipos de matrices multidimensionales. Consulte [matrices escalonadas](http://go.microsoft.com/fwlink/?LinkId=195226) y [matrices multidimensionales](http://go.microsoft.com/fwlink/?LinkId=195227) para obtener más información.  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
1.  En el **nombre de tipo** , escriba el nombre del tipo que desea usar.  
  
2.  Realice una de las siguientes acciones:  
  
    -   Cuando aparezca el nombre del tipo que se va a usar en el árbol en el **nombre de tipo** cuadro, haga doble clic en el tipo para seleccionarlo.  
  
    -   Escriba los caracteres suficientes en el **nombre de tipo** cuadro para identificar de forma única el tipo que desea usar y, a continuación, presione ENTRAR para seleccionar el tipo  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para seleccionar un tipo genérico en el explorador de tipo  
  
1.  En el **nombre de tipo** cuadro, escriba el nombre del tipo que desea usar.  
  
2.  Cuando aparezca el nombre del tipo que se va a usar en el árbol en el **nombre de tipo** cuadro, haga clic en el tipo para seleccionarla y hacer que los cuadros de lista desplegable aparezca.  
  
     Seleccione el tipo que desea usar para cerrar el genérico en los cuadros de lista desplegable y, a continuación, haga clic en **Aceptar**.  
  
## <a name="types-displayed-in-the-type-browser"></a>Tipos que se muestran en el explorador de tipo  
 Los tipos que se muestran en el explorador pueden variar en función de cómo se haya iniciado el explorador de tipo. Si el Explorador de tipos se inició desde un proyecto de flujo de trabajo dentro de **vs2010**, de forma predeterminada todos los tipos en los ensamblados de referencia y se muestran los proyectos que se hace referencia. Si el Explorador de tipos se inició desde fuera de un **vs2010** proyecto del sistema (por ejemplo, al igual que en una aplicación de flujo de trabajo hospedado en otro host o en un archivo de flujo de trabajo independiente), a continuación, de forma predeterminada se muestran los tipos de todos los ensamblados cargados en el dominio de aplicación .  
  
 Los tipos en el explorador de tipo se pueden filtrar por desarrolladores de software del diseñador de actividades. Respecto a una actividad en concreto, es posible que vea únicamente un subconjunto de los tipos. Por ejemplo, en la actividad <xref:System.Activities.Statements.TryCatch>, solo se muestran los tipos derivados de <xref:System.Exception> en el explorador de tipo.  
  
## <a name="filtering-search-results-in-the-type-browser"></a>Filtrar los resultados de la búsqueda en el explorador de tipo  
 La lista de tipos en el **nombre de tipo** cuadro obtiene más corto a medida que escribe más caracteres para buscar una coincidencia. Solo aparecerán en la lista filtrada los tipos cuyo nombre completo o cuyo nombre corto comiencen con la cadena que ha escrito.  
  
 Por ejemplo:  
  
1.  Escriba **operación** coincide con <xref:System.OperationCanceledException> pero no <xref:System.InvalidOperationException>. Para buscar coincidencias con <xref:System.InvalidOperationException>, comience a escribir System.I o Invalid.  
  
2.  Escriba **genérico** coincide con <xref:System.GenericUriParser> pero no con los tipos en el <xref:System.Collections.Generic> espacio de nombres. Para buscar tipos en el espacio de nombres <xref:System.Collections.Generic>, escriba el nombre completo del espacio de nombres.  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Seleccionar un contrato de servicio usando el cuadro de diálogo de explorador de tipo  
 Al seleccionar un tipo de contrato de servicio, el explorador de tipo muestra únicamente los tipos que tienen el atributo <xref:System.ServiceModel.ServiceContractAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)