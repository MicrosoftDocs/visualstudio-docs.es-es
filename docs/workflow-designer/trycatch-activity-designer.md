---
title: "Dise&#241;ador de actividades TryCatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades TryCatch
El diseñador de actividades **TryCatch** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.TryCatch>.  
  
## Actividad TryCatch  
 La actividad <xref:System.Activities.Statements.TryCatch> contiene una actividad <xref:System.Activities.Statements.TryCatch.Try%2A>, una colección de propiedades <xref:System.Activities.Statements.TryCatch.Finally%2A> y una actividad **Catch\<TException\>**.Una clase <xref:System.Activities.Statements.Catch%601> de tipo **TException** contiene una propiedad <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> y otra propiedad <xref:System.Activities.Statements.Catch%601.Action%2A>.Todas ellas se utilizan para implementar un mecanismo típico de control de errores basado en excepciones.Una actividad <xref:System.Activities.Statements.TryCatch> intenta ejecutar su actividad <xref:System.Activities.Statements.TryCatch.Try%2A>.Si la actividad <xref:System.Activities.Statements.TryCatch.Try%2A> produce algún tipo de excepción, la actividad <xref:System.Activities.Statements.TryCatch> utiliza su colección **Catch\<TException\>** para buscar una coincidencia para la excepción.Si se encuentra una coincidencia, se ejecuta la propiedad <xref:System.Activities.Statements.Catch%601.Action%2A> de la clase **Catch\<TException\>** correspondiente, lo cual se utiliza como la lógica de control de errores para la excepción.Si las actividades de la sección <xref:System.Activities.Statements.TryCatch.Try%2A> se completan correctamente o las actividades de <xref:System.Activities.Statements.TryCatch.Catches%2A> se completan correctamente, la actividad <xref:System.Activities.Statements.TryCatch> ejecuta su actividad <xref:System.Activities.Statements.TryCatch.Finally%2A>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Excepciones](../Topic/Exceptions.md).  
  
### Utilizar el diseñador de actividades TryCatch  
 El diseñador de actividades **TryCatch** se puede encontrar en la categoría **Control de errores** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X.\)  
  
 El diseñador de actividades **TryCatch** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.TryCatch> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TryCatch.El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **TryCatch** o en el cuadro **DisplayName** de la cuadrícula de propiedades.Las otras propiedades deben editarse en la superficie del diseñador de actividades **TryCatch**.  
  
 Haga clic en el botón para expandir en la esquina superior derecha del diseñador **TryCatch** para ver los cuadros **Try**, **Catches** y **Finally** en la vista expandida.Para agregar una instrucción catch, haga clic en el botón **Agregar nueva instrucción catch** en el diseñador **TryCatch**.El botón cambia a un cuadro combinado de tipo.Seleccione un tipo de excepción y presione ENTRAR para agregar la instrucción catch.Una vez haya agregado una instrucción **Catch**, el área de captura se expande y se puede colocar una actividad en la instrucción catch para definir la lógica de ejecución de esta instrucción.Observe que hay un cuadro de texto a la derecha del área de la instrucción catch expandida.Puede asignar un nombre a la variable de excepción con este cuadro de texto.La variable de excepción solo se puede utilizar para las actividades en la misma instrucción **Catch**.  
  
 El diseñador **TryCatch** no admite la edición de **Catch**.Si desea cambiar el tipo de excepción, tiene que eliminar la instrucción **Catch** y agregar una nueva.**Catch** se puede eliminar si la selecciona y elimina o mediante el menú **Eliminar** del menú contextual que aparece cuando se hace clic con el botón secundario del mouse.  
  
### Propiedades TryCatch  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TryCatch> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.TryCatch>.El valor predeterminado es TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|La actividad se ejecuta primero cuando <xref:System.Activities.Statements.TryCatch> se ejecuta.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|La colección de elementos **Catch** que se va a comprobar cuando la actividad <xref:System.Activities.Statements.TryCatch.Try%2A> produzca una excepción.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|La actividad que se va a ejecutar cuando la clase <xref:System.Activities.Statements.TryCatch.Try%2A> y cualquiera de las actividades necesarias en la colección <xref:System.Activities.Statements.TryCatch.Catches%2A> completen la ejecución.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)