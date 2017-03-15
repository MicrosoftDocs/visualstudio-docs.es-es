---
title: "Examinar y seleccionar un cuadro de di&#225;logo de tipo .NET | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeBrowser.UI"
  - "ActivityTypeResolver.UI"
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
caps.handback.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Examinar y seleccionar un cuadro de di&#225;logo de tipo .NET
En la ventana **Propiedades**, cuadros de diálogo o diseñadores como el diseñador de variables, cuando selecciona **Buscar tipos** en una lista de tipos de datos, está el cuadro de diálogo **Examinar y seleccionar un tipo .NET** \(al que se hace referencia de forma abreviada como "tipo de explorador"\).En este cuadro de diálogo, puede escoger un tipo en una vista de árbol de ensamblados y proyectos.  
  
 Este cuadro de diálogo se emplea en varios escenarios de usuario, lo cual incluye lo siguiente:  
  
-   Cuando se establece el tipo de una variable o argumento.  
  
-   Cuando se selecciona un tipo para una actividad genérica.  
  
-   Cuando se agrega una instrucción catch en la actividad <xref:System.Activities.Statements.TryCatch>.  
  
> [!NOTE]
>  El explorador de tipo puede mostrar tipos de matrices escalonadas Visual Basic de matriz, pero no tipos de matrices multidimensionales.Vea [Matrices escalonadas](http://go.microsoft.com/fwlink/?LinkId=195226) y [Matrices multidimensionales](http://go.microsoft.com/fwlink/?LinkId=195227) para obtener detalles.  
  
## Seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
#### Para seleccionar un tipo de valor y de referencia en el explorador de tipo  
  
1.  En el cuadro **Nombre de tipo**, escriba el nombre del tipo que desee utilizar.  
  
2.  Siga uno de los procedimientos siguientes:  
  
    -   Cuando aparezca el nombre del tipo que desea utilizar en el árbol en el cuadro **Nombre de tipo**, haga doble clic en el tipo para seleccionarlo.  
  
    -   Escriba los caracteres suficientes en el cuadro **Nombre de tipo** para identificar de forma única el tipo que desea utilizar y, a continuación, presione Entrar para seleccionar el tipo.  
  
#### Para seleccionar un tipo genérico en el explorador de tipo  
  
1.  En el cuadro **Nombre de tipo**, escriba el nombre del tipo que desee utilizar.  
  
2.  Cuando aparezca el nombre del tipo que desea utilizar en el árbol en el cuadro **Nombre de tipo**, haga doble clic en el tipo para seleccionarlo y que aparezcan los cuadros desplegables.  
  
     Seleccione el tipo que desea utilizar para cerrar el genérico en los cuadros desplegables y, a continuación, haga clic en **Aceptar**.  
  
## Tipos que se muestran en el explorador de tipo  
 Los tipos que se muestran en el explorador pueden variar en función de cómo se haya iniciado el explorador de tipo.Si se inició desde un proyecto de flujo de trabajo en **vs2010**, de forma predeterminada se muestran todos los tipos en los ensamblados y proyectos referenciados.Si el explorador de tipo se inició fuera de un sistema de proyectos de **vs2010** \(como en una aplicación de flujo de trabajo hospedada en otro host o en un archivo de flujo de trabajo independiente\), a continuación, de forma predeterminada se muestran los tipos de todos los ensamblados que se cargaron en AppDomain.  
  
 Los tipos en el explorador de tipo se pueden filtrar por desarrolladores de software del diseñador de actividades.Respecto a una actividad en concreto, es posible que vea únicamente un subconjunto de los tipos.Por ejemplo, en la actividad <xref:System.Activities.Statements.TryCatch>, solo se muestran los tipos derivados de <xref:System.Exception> en el explorador de tipo.  
  
## Filtrar los resultados de la búsqueda en el explorador de tipo  
 La lista de tipos en el cuadro **Nombre de tipo** se va reduciendo según se escriben más caracteres para encontrar una coincidencia.Solo aparecerán en la lista filtrada los tipos cuyo nombre completo o cuyo nombre corto comiencen con la cadena que ha escrito.  
  
 Por ejemplo:  
  
1.  Si escribe **Operation** coincidirá con <xref:System.OperationCanceledException> pero no con <xref:System.InvalidOperationException>.Para buscar coincidencias con <xref:System.InvalidOperationException>, comience a escribir System.I o Invalid.  
  
2.  Si escribe **Generic** coincidirá con <xref:System.GenericUriParser> pero no con los tipos en el espacio de nombres <xref:System.Collections.Generic>.Para buscar tipos en el espacio de nombres <xref:System.Collections.Generic>, escriba el nombre completo del espacio de nombres.  
  
## Seleccionar un contrato de servicio usando el cuadro de diálogo de explorador de tipo  
 Al seleccionar un tipo de contrato de servicio, el explorador de tipo muestra únicamente los tipos que tienen el atributo <xref:System.ServiceModel.ServiceContractAttribute>.  
  
## Vea también  
 [Utilizar los diseñadores de actividades](../workflow-designer/using-the-activity-designers.md)