---
title: "Utilizar el dise&#241;ador de importaciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Utilizar el dise&#241;ador de importaciones
El diseñador de importaciones le permite escribir los espacios de nombres para los tipos que utilizará en sus expresiones.Como sucede en gran medida con las palabras clave **Imports** o **using** en Visual Basic .NET y C\#, la especificación de espacios de nombres en el diseñador de importaciones le permite escribir simplemente un nombre de tipo en su expresión en lugar de un nombre de tipo de versión completo.  
  
 El diseñador de importaciones reacciona tanto a los cambios en la interfaz de usuario como a los cambios que se efectúan cuando se guarda el flujo de trabajo.Cuando el flujo de trabajo está guardado, los espacios de nombres se pueden agregar automáticamente al diseñador de importaciones.Lo cual incluye lo siguiente:  
  
-   Espacios de nombres para cualquier tipo utilizado en declaraciones de variables y de argumentos.  
  
-   Espacios de nombres para cualquier tipo utilizado en expresiones.  
  
-   Cualquier otro espacio de nombres que se necesite para serializar el flujo de trabajo \(por ejemplo, espacios de nombres utilizados por actividades personalizadas que se hayan colocado en el flujo de trabajo\).  
  
 Cuando se guarda el flujo de trabajo, podría observar que algunos espacios de nombres que ha eliminado manualmente se vuelven a agregar automáticamente al diseñador de importaciones debido a la lógica descrita en la lista anterior.  
  
### Para agregar un espacio de nombres a la lista de espacios de nombres importados  
  
1.  Abra una aplicación de servicio de WCF, una aplicación de consola del flujo de trabajo, un proyecto de biblioteca de actividades en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] o una aplicación de flujo de trabajo hospedada en otro host.  
  
2.  Haga clic en **Importaciones** en la parte inferior del lienzo principal.Aparecerá el diseñador de importaciones.  
  
3.  Escriba o seleccione un espacio de nombres desde el control de lista desplegable en la parte superior del diseñador de importaciones.  
  
     Cuando escriba, aparecerá una lista de espacios de nombres válidos que coinciden con los caracteres que se van escribiendo.  
  
4.  Presione **Entrar** para agregar el espacio de nombres a la lista.  
  
5.  Si desea quitar un espacio de nombres de la lista, seleccione el espacio de nombres y, a continuación, presione la tecla **Suprimir** del teclado.Observe que un espacio de nombres solo se puede eliminar si el espacio de nombres no es válido por cualquier razón, por ejemplo si el proyecto ya no hace referencia al ensamblado que contiene el espacio de nombres.